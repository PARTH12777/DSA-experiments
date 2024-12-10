#include <stdio.h>
#include <stdlib.h>

struct Stack {
    int data;
    struct Stack* next;
};

struct Stack* newNode(int data) {
    struct Stack* node = (struct Stack*)malloc(sizeof(struct Stack));
    node->data = data;
    node->next = NULL;
    return node;
}

int isEmpty(struct Stack* root) {
    return !root;
}

void push(struct Stack** root, int data) {
    struct Stack* stackNode = newNode(data);
    stackNode->next = *root;
    *root = stackNode;
}

int pop(struct Stack** root) {
    if (isEmpty(*root))
        return -1;
    struct Stack* temp = *root;
    *root = (*root)->next;
    int popped = temp->data;
    free(temp);
    return popped;
}

int peek(struct Stack* root) {
    if (isEmpty(root))
        return -1;
    return root->data;
}

void insertAtBottom(struct Stack** root, int item) {
    if (isEmpty(*root)) {
        push(root, item);
        return;
    }
    int temp = pop(root);
    insertAtBottom(root, item);
    push(root, temp);
}

void reverseStack(struct Stack** root) {
    if (!isEmpty(*root)) {
        int temp = pop(root);
        reverseStack(root);
        insertAtBottom(root, temp);
    }
}

void printStack(struct Stack* root) {
    while (root) {
        printf("%d ", root->data);
        root = root->next;
    }
    printf("\n");
}

int main() {
    struct Stack* stack = NULL;
    push(&stack, 1);
    push(&stack, 2);
    push(&stack, 3);
    push(&stack, 4);
    
    printStack(stack);
    reverseStack(&stack);
    printStack(stack);
    
    return 0;
}
