#include <stdio.h>

struct Employee {
    int id;
    char name[50];
    char designation[50];
    float basic;
};

int main() {
    struct Employee emp;
    float hra, da, pf, gross, net;
    FILE *fp;

    printf("Enter Employee ID: ");
    scanf("%d", &emp.id);

    printf("Enter Employee Name: ");
    scanf(" %[^\n]", emp.name);

    printf("Enter Designation: ");
    scanf(" %[^\n]", emp.designation);

    printf("Enter Basic Salary: ");
    scanf("%f", &emp.basic);

    hra = emp.basic * 0.20;   // 20% HRA
    da  = emp.basic * 0.10;   // 10% DA
    pf  = emp.basic * 0.12;   // 12% PF

    gross = emp.basic + hra + da;
    net = gross - pf;

    fp = fopen("salary_slip.txt", "w");

    fprintf(fp, "-------------------------------\n");
    fprintf(fp, "       SALARY SLIP\n");
    fprintf(fp, "-------------------------------\n");
    fprintf(fp, "Employee ID   : %d\n", emp.id);
    fprintf(fp, "Name          : %s\n", emp.name);
    fprintf(fp, "Designation   : %s\n", emp.designation);
    fprintf(fp, "-------------------------------\n");
    fprintf(fp, "Basic Salary  : %.2f\n", emp.basic);
    fprintf(fp, "HRA (20%%)     : %.2f\n", hra);
    fprintf(fp, "DA (10%%)      : %.2f\n", da);
    fprintf(fp, "PF (12%%)      : %.2f\n", pf);
    fprintf(fp, "-------------------------------\n");
    fprintf(fp, "Gross Salary  : %.2f\n", gross);
    fprintf(fp, "Net Salary    : %.2f\n", net);
    fprintf(fp, "-------------------------------\n");

    fclose(fp);

    printf("\nSalary slip generated successfully!");
    printf("\nCheck 'salary_slip.txt' file.\n");

    return 0;
}
