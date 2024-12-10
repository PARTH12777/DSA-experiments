#include <stdio.h>
#include <string.h>

#define MAX_CUSTOMERS 100

typedef struct {
    char name[50];
} Customer;

typedef struct {
    Customer customers[MAX_CUSTOMERS];
    int front; // Index of the front of the queue
    int rear;  // Index of the rear of the queue
} CustomerQueue;

void initializeQueue(CustomerQueue* queue) {
    queue->front = -1;
    queue->rear = -1;
}

int isFull(CustomerQueue* queue) {
    return queue->rear == MAX_CUSTOMERS - 1;
}

int isEmpty(CustomerQueue* queue) {
    return queue->front == -1 || queue->front > queue->rear;
}

void enqueue(CustomerQueue* queue, const char* name) {
    if (isFull(queue)) {
        printf("Queue is full. Cannot add more customers.\n");
        return;
    }
    if (isEmpty(queue)) {
        queue->front = 0; // Set front to 0 if queue was empty
    }
    queue->rear++;
    strcpy(queue->customers[queue->rear].name, name);
    printf("Customer '%s' added to the queue.\n", name);
}

void dequeue(CustomerQueue* queue) {
    if (isEmpty(queue)) {
        printf("Queue is empty. No customers to serve.\n");
        return;
    }
    printf("Customer '%s' has been served.\n", queue->customers[queue->front].name);
    queue->front++;
}

void peek(CustomerQueue* queue) {
    if (isEmpty(queue)) {
        printf("Queue is empty. No customers to view.\n");
        return;
    }
    printf("Customer at the front of the queue: '%s'\n", queue->customers[queue->front].name);
}

void displayQueue(CustomerQueue* queue) {
    if (isEmpty(queue)) {
        printf("Queue is empty. No customers to display.\n");
        return;
    }
    printf("Customers in the queue:\n");
    for (int i = queue->front; i <= queue->rear; i++) {
        printf("%d. %s\n", i - queue->front + 1, queue->customers[i].name);
    }
}


int main() {
    CustomerQueue queue;
    initializeQueue(&queue);
    
    int choice;
    char name[50];

    do {
        printf("\nCustomer Service Queue Management System\n");
        printf("1. Enqueue a customer\n");
        printf("2. Dequeue a customer\n");
        printf("3. Peek at the front customer\n");
        printf("4. Display all customers\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        getchar(); 

        switch (choice) {
            case 1:
                printf("Enter the name of the customer: ");
                fgets(name, sizeof(name), stdin);
                name[strcspn(name, "\n")] = 0; // Remove newline character
                enqueue(&queue, name);
                break;
            case 2:
                dequeue(&queue);
                break;
            case 3:
                peek(&queue);
                break;
            case 4:
                displayQueue(&queue);
                break;
            case 5:
                printf("Exiting the program. Goodbye!\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 5);

    return 0;
}
