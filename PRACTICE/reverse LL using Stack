#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* newNode(int data) {
    struct Node* node = (struct Node*)malloc(sizeof(struct Node));
    node->data = data;
    node->next = NULL;
    return node;
}

void push(struct Node** top_ref, int data) {
    struct Node* new_node = newNode(data);
    new_node->next = *top_ref;
    *top_ref = new_node;
}

int pop(struct Node** top_ref) {
    if (*top_ref == NULL) {
        exit(1);
    }
    struct Node* temp = *top_ref;
    *top_ref = (*top_ref)->next;
    int popped_data = temp->data;
    free(temp);
    return popped_data;
}

void reverseLinkedList(struct Node** head_ref) {
    struct Node* stack = NULL;
    struct Node* current = *head_ref;
    
    while (current != NULL) {
        push(&stack, current->data);
        current = current->next;
    }
    
    current = *head_ref;
    
    while (current != NULL) {
        current->data = pop(&stack);
        current = current->next;
    }
}

void printList(struct Node* head) {
    struct Node* temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

int main() {
    struct Node* head = NULL;
    
    head = newNode(1);
    head->next = newNode(2);
    head->next->next = newNode(3);
    head->next->next->next = newNode(4);
    
    printf("Original Linked List:\n");
    printList(head);
    
    reverseLinkedList(&head);
    
    printf("\nReversed Linked List:\n");
    printList(head);
    
    return 0;
}

 
