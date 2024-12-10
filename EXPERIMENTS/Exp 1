#include <stdio.h>

#define MAX_SIZE 100

void insertAtBeginning(int arr[], int *n, int element);
void insertAtEnd(int arr[], int *n, int element);
void insertAtPosition(int arr[], int *n, int element, int position); 
void displayArray(int arr[], int n);

int main()
{
    int arr[MAX_SIZE], n, choice, element, position;

    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    printf("Enter the elements of the array:\n");
    for (int i = 0; i < n; i++)
    {
        scanf("%d", &arr[i]);
    }

    do
    {

        printf("\nMenu:\n");
        printf("1. Insert at Beginning\n");
        printf("2. Insert at End\n");
        printf("3. Insert at Specific Position\n");
        printf("4. Display Array\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice)
        {
        case 1:
            printf("Enter element to insert at the beginning: ");
            scanf("%d", &element);
            insertAtBeginning(arr, &n, element);
            printf("Element added at the beginning.\n");
            displayArray(arr, n);
            break;
        case 2:
            printf("Enter element to insert at the end: ");
            scanf("%d", &element);
            insertAtEnd(arr, &n, element);
            printf("Element added at the end.\n");
            displayArray(arr, n);
            break;
        case 3:
            printf("Enter element to insert: ");
            scanf("%d", &element);
            printf("Enter position (1 to %d): ", n + 1);
            scanf("%d", &position);
            if (position >= 1 && position <= n + 1)
            {
                insertAtPosition(arr, &n, element, position);
                printf("Element added at position %d.\n", position);
                displayArray(arr, n);
            }
            else
            {
                printf("Invalid position!\n");
            }
            break;
        case 4:
            displayArray(arr, n);
            break;
        case 5:
            printf("Exiting...\n");
            break;
        default:
            printf("Invalid choice!\n");
        }
    } while (choice != 5);

    return 0;
}

void insertAtBeginning(int arr[], int *n, int element)
{
    for (int i = *n; i > 0; i--)
    {
        arr[i] = arr[i - 1];
    }
    arr[0] = element;

        (*n)++;
}

void insertAtEnd(int arr[], int *n, int element)
{
    arr[*n] = element;
    (*n)++;
}

void insertAtPosition(int arr[], int *n, int element, int position)
{
    for (int i = *n; i >= position; i--)
    {
        arr[i] = arr[i - 1];
    }
    arr[position - 1] = element;
    (*n)++;
}

void displayArray(int arr[], int n)
{
    printf("Array elements: ");
    for (int i = 0; i < n; i++)
    {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
