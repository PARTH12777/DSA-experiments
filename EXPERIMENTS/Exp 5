#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct Task {
    int id;
    char description[100];
    char status[10];
    struct Task* next;
} Task;

Task* createTask(int id, const char* description) {
    Task* newTask = (Task*)malloc(sizeof(Task));
    newTask->id = id;
    strcpy(newTask->description, description);
    strcpy(newTask->status, "Pending");
    newTask->next = NULL;
    return newTask;
}

void addTask(Task** head, int id, const char* description) {
    Task* newTask = createTask(id, description);
    if (*head == NULL) {
        *head = newTask;
    } else {
        Task* current = *head;
        while (current->next != NULL) {
            current = current->next;
        }
        current->next = newTask;
    }
    printf("Task '%s' added with ID %d.\n", description, id);
}

void removeTask(Task** head, int id) {
    if (*head == NULL) {
        printf("No tasks available to remove.\n");
        return;
    }

    Task* current = *head;
    Task* previous = NULL;

    while (current != NULL && current->id != id) {
        previous = current;
        current = current->next;
    }

    if (current == NULL) {
        printf("Task with ID %d not found.\n", id);
        return;
    }

    if (previous == NULL) {
        *head = current->next;
    } else {
        previous->next = current->next;
    }
    free(current);
    printf("Task with ID %d removed.\n", id);
}

void markTaskAsCompleted(Task* head, int id) {
    Task* current = head;
    while (current != NULL) {
        if (current->id == id) {
            strcpy(current->status, "Completed");
            printf("Task with ID %d marked as completed.\n", id);
            return;
        }
        current = current->next;
    }
    printf("Task with ID %d not found.\n", id);
}

void displayTasks(Task* head) {
    if (head == NULL) {
        printf("No tasks available.\n");
        return;
    }

    printf("Current Tasks:\n");
    Task* current = head;
    while (current != NULL) {
        printf("ID: %d, Description: '%s', Status: '%s'\n", current->id, current->description, current->status);
        current = current->next;
    }
}

int main() {
    Task* taskList = NULL;
    int choice, id;
    char description[100];

    do {
        printf("\nTask Management System\n");
        printf("1. Add Task\n");
        printf("2. Remove Task\n");
        printf("3. Mark Task as Completed\n");
        printf("4. Display Tasks\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        getchar();

        switch (choice) {
            case 1:
                printf("Enter Task ID: ");
                scanf("%d", &id);
                getchar();
                printf("Enter Task Description: ");
                fgets(description, sizeof(description), stdin);
                description[strcspn(description, "\n")] = 0;
                addTask(&taskList, id, description);
                break;
            case 2:
                printf("Enter Task ID to remove: ");
                scanf("%d", &id);
                removeTask(&taskList, id);
                break;
            case 3:
                printf("Enter Task ID to mark as completed: ");
                scanf("%d", &id);
                markTaskAsCompleted(taskList, id);
                break;
            case 4:
                displayTasks(taskList);
                break;
            case 5:
                printf("Exiting the program. Goodbye!\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 5);

    while (taskList != NULL) {
        Task* temp = taskList;
        taskList = taskList->next;
        free(temp);
    }

    return 0;
}
