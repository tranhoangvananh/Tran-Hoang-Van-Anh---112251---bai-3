#include <stdio.h>
#include <stdlib.h>
#include <string.h>
typedef struct {
    char hoTen[50];
    char ma[20];
    float diem1, diem2, diem3;
} SinhVien;
void xoaBoNhoDem() {
    int c;
    while ((c = getchar()) != '\n' && c != EOF);
}
int main() {
    int n;
    printf("Nhap so luong sinh vien: ");
    scanf("%d", &n);
    xoaBoNhoDem();
    if (n <= 0) {
        printf("So luong sinh vien phai lon hon 0!\n");
        return 1;
    }
    SinhVien *ds = malloc((size_t)n * sizeof(SinhVien));
    if (ds == NULL) {
        printf("Khong du bo nho!\n");
        return 1;
    }
    for (int i = 0; i < n; i++) {
        printf("\n--- Nhap thong tin sinh vien thu %d ---\n", i + 1);
        printf("Ho ten: ");
        fgets((ds + i)->hoTen, sizeof((ds + i)->hoTen), stdin);
        (ds + i)->hoTen[strcspn((ds + i)->hoTen, "\n")] = '\0';
        printf("Ma SV: ");
        fgets((ds + i)->ma, sizeof((ds + i)->ma), stdin);
        (ds + i)->ma[strcspn((ds + i)->ma, "\n")] = '\0';
        printf("Diem 1, Diem 2, Diem 3: ");
        scanf("%f %f %f", &(ds + i)->diem1, &(ds + i)->diem2, &(ds + i)->diem3);
        xoaBoNhoDem();
    }
    printf("\n%-25s %-15s %-8s %-8s %-8s\n", "Ho Ten", "Ma SV", "Diem 1", "Diem 2", "Diem 3");
    for (int i = 0; i < n; i++) {
        printf("%-25s %-15s %-8.2f %-8.2f %-8.2f\n",
               (ds + i)->hoTen, (ds + i)->ma,
               (ds + i)->diem1, (ds + i)->diem2, (ds + i)->diem3);
    }
    free(ds);
    ds = NULL;
    return 0;
}
