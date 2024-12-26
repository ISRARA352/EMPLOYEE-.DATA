# EMPLOYEE-.DATA
#include <stdio.h>
#include <string.h>

// Define a structure to store employee details
struct Employee {
    int id;
    char name[100];
    int age;
    float salary;
};

// Function to input employee data
void inputEmployeeData(struct Employee *emp) {
    printf("Enter Employee ID: ");
    scanf("%d", &emp->id);
    getchar();  // To consume the newline character after scanf

    printf("Enter Employee Name: ");
    fgets(emp->name, sizeof(emp->name), stdin);
    emp->name[strcspn(emp->name, "\n")] = 0;  // Remove the newline character

    printf("Enter Employee Age: ");
    scanf("%d", &emp->age);

    printf("Enter Employee Salary: ");
    scanf("%f", &emp->salary);
}

// Function to display employee data
void displayEmployeeData(struct Employee emp) {
    printf("\nEmployee ID: %d\n", emp.id);
    printf("Employee Name: %s\n", emp.name);
    printf("Employee Age: %d\n", emp.age);
    printf("Employee Salary: %.2f\n", emp.salary);
}

int main() {
    int n;

    // Asking for the number of employees
    printf("Enter the number of employees: ");
    scanf("%d", &n);

    // Declare an array of Employee structures
    struct Employee employees[n];

    // Input data for all employees
    for (int i = 0; i < n; i++) {
        printf("\nEnter details for Employee %d:\n", i + 1);
        inputEmployeeData(&employees[i]);
    }

    // Display data for all employees
    printf("\nEmployee Data:\n");
    for (int i = 0; i < n; i++) {
        printf("\nDetails of Employee %d:\n", i + 1);
        displayEmployeeData(employees[i]);
    }

    return 0;
}
