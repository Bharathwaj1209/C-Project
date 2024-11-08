#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Define the structure for a node in the singly linked list
struct Node {
    char name[100];
    char phone[15];
    char email[100];
    struct Node* next;
};
typedef struct Node* NODE;

// Function to add a new entry to the address book
void addEntry(NODE* head_ref, char* name, char* phone, char* email) {
    NODE new_node = (NODE) malloc(sizeof(struct Node));
    strcpy(new_node->name, name);
    strcpy(new_node->phone, phone);
    strcpy(new_node->email, email);
    new_node->next = (*head_ref);
    *head_ref = new_node;
}

// Function to delete an entry from the address book
void deleteEntry(NODE* head_ref, char* name) {
    NODE temp = *head_ref;
    NODE prev = NULL;

    // If head node itself holds the entry to be deleted
    if (temp != NULL && strcmp(temp->name, name) == 0) {
        *head_ref = temp->next;
        free(temp);
        return;
    }

    // Search for the entry to be deleted
    while (temp != NULL && strcmp(temp->name, name) != 0) {
        prev = temp;
        temp = temp->next;
    }

    // If entry was not present in the list
    if (temp == NULL) return;

    // Unlink the node from the linked list
    prev->next = temp->next;

    free(temp);
}

// Function to search for an entry in the address book
void searchEntry(NODE head, char* name) {
    NODE current = head;
    while (current != NULL) {
        if (strcmp(current->name, name) == 0) {
            printf("Found entry:\n");
            printf("Name: %s\n", current->name);
            printf("Phone: %s\n", current->phone);
            printf("Email: %s\n", current->email);
            return;
        }
        current = current->next;
    }
    printf("Entry not found\n");
}

// Function to display all entries in the address book
void displayEntries(NODE head) {
    NODE current = head;
    while (current != NULL) {
        printf("Name: %s\n", current->name);
        printf("Phone: %s\n", current->phone);
        printf("Email: %s\n", current->email);
        current = current->next;
    }
}

// Function to free the entire list
void freeList(NODE head) {
    NODE temp;
    while (head != NULL) {
        temp = head;
        head = head->next;
        free(temp);
    }
}

int main() {
    NODE head = NULL;
    int choice;
    char name[100], phone[15], email[100];

    while (1) {
        printf("\nAddress Book Menu\n");
        printf("1. Add Entry\n");
        printf("2. Delete Entry\n");
        printf("3. Search Entry\n");
        printf("4. Display All Entries\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter name: ");
                scanf("%s", name);
                printf("Enter phone: ");
                scanf("%s", phone);
                printf("Enter email: ");
                scanf("%s", email);
                addEntry(&head, name, phone, email);
                break;
            case 2:
                printf("Enter name to delete: ");
                scanf("%s", name);
                deleteEntry(&head, name);
                break;
            case 3:
                printf("Enter name to search: ");
                scanf("%s", name);
                searchEntry(head, name);
                break;
}
