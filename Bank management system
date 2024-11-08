#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Structure to store customer details
typedef struct Customer {
    int customerID;
    char name[100];
    char address[200];
    char phone[15];
} Customer;

// Structure to store account details
typedef struct Account {
    int accountNumber;
    Customer customer;
    double balance;
    struct Account* next;
} Account;

// Head of the linked list of accounts
Account* head = NULL;

// Function to create a new account
Account* createAccount(int accountNumber, Customer customer, double initialBalance) {
    Account* newAccount = (Account*)malloc(sizeof(Account));
    newAccount->accountNumber = accountNumber;
    newAccount->customer = customer;
    newAccount->balance = initialBalance;
    newAccount->next = NULL;
    return newAccount;
}

// Function to add a new account to the linked list
void addAccount(Account* account) {
    if (head == NULL) {
        head = account;
    } else {
        Account* temp = head;
        while (temp->next != NULL) {
            temp = temp->next;
        }
        temp->next = account;
    }
}

// Function to find an account by account number
Account* findAccount(int accountNumber) {
    Account* temp = head;
    while (temp != NULL) {
        if (temp->accountNumber == accountNumber) {
            return temp;
        }
        temp = temp->next;
    }
    return NULL;
}

// Function to deposit money into an account
void deposit(int accountNumber, double amount) {
    Account* account = findAccount(accountNumber);
    if (account != NULL) {
        account->balance += amount;
        printf("Deposit successful. New balance: %.2f\n", account->balance);
    } else {
        printf("Account not found.\n");
    }
}

// Function to withdraw money from an account
void withdraw(int accountNumber, double amount) {
    Account* account = findAccount(accountNumber);
    if (account != NULL) {
        if (account->balance >= amount) {
            account->balance -= amount;
            printf("Withdrawal successful. New balance: %.2f\n", account->balance);
        } else {
            printf("Insufficient funds.\n");
        }
    } else {
        printf("Account not found.\n");
    }
}

// Function to check the balance of an account
void checkBalance(int accountNumber) {
    Account* account = findAccount(accountNumber);
    if (account != NULL) {
        printf("Current balance: %.2f\n", account->balance);
    } else {
        printf("Account not found.\n");
    }
}

// Function to display all accounts
void displayAccounts() {
    Account* temp = head;
    while (temp != NULL) {
        printf("Account Number: %d\n", temp->accountNumber);
        printf("Customer ID: %d\n", temp->customer.customerID);
        printf("Customer Name: %s\n", temp->customer.name);
        printf("Balance: %.2f\n", temp->balance);
        printf("\n");
        temp = temp->next;
    }
}

// Function to get customer details from the user
Customer getCustomerDetails() {
    Customer customer;
    printf("Enter customer ID: ");
    scanf("%d", &customer.customerID);
    printf("Enter customer name: ");
    getchar(); // to consume the newline character left by scanf
    fgets(customer.name, sizeof(customer.name), stdin);
    customer.name[strcspn(customer.name, "\n")] = '\0'; // remove the newline character
    printf("Enter customer address: ");
    fgets(customer.address, sizeof(customer.address), stdin);
    customer.address[strcspn(customer.address, "\n")] = '\0'; // remove the newline character
    printf("Enter customer phone: ");
    fgets(customer.phone, sizeof(customer.phone), stdin);
    customer.phone[strcspn(customer.phone, "\n")] = '\0'; // remove the newline character
    return customer;
}

// Main function
int main() {
    int choice, accountNumber;
    double amount;
    Customer customer;
    Account* account;

    while (1) {
        printf("\nBank Management System\n");
        printf("1. Create Account\n");
        printf("2. Deposit\n");
        printf("3. Withdraw\n");
        printf("4. Check Balance\n");
        printf("5. Display All Accounts\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter account number: ");
                scanf("%d", &accountNumber);
                customer = getCustomerDetails();
                printf("Enter initial balance: ");
                scanf("%lf", &amount);
                account = createAccount(accountNumber, customer, amount);
                addAccount(account);
                break;
            case 2:
                printf("Enter account number: ");
                scanf("%d", &accountNumber);
                printf("Enter amount to deposit: ");
                scanf("%lf", &amount);
                deposit(accountNumber, amount);
                break;
            case 3:
                printf("Enter account number: ");
                scanf("%d", &accountNumber);
                printf("Enter amount to withdraw: ");
                scanf("%lf", &amount);
                withdraw(accountNumber, amount);
                break;
            case 4:
                printf("Enter account number: ");
                scanf("%d", &accountNumber);
                checkBalance(accountNumber);
                break;
            case 5:
                displayAccounts();
                break;
            case 6:
                exit(0);
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}
