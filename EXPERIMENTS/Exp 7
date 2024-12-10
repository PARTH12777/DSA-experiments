#include <stdio.h>
#define MAX_SIZE 15

void displayTree(int tree[], int size) {
    printf("Tree:\n");
    for (int i = 0; i < size; i++) {
        if (tree[i] != -1) { 
            printf("Node %d: %d\n", i, tree[i]);
            int leftIndex = 2 * i + 1;
            int rightIndex = 2 * i + 2;
            if (leftIndex < size && tree[leftIndex] != -1)
                printf("  Left child: %d\n", tree[leftIndex]);
            if (rightIndex < size && tree[rightIndex] != -1)
                printf("  Right child: %d\n", tree[rightIndex]);
        }
    }
}

void preOrder(int tree[], int index, int size) {
    if (index >= size || tree[index] == -1) return;
    printf("%d ", tree[index]);
    preOrder(tree, 2 * index + 1, size);
    preOrder(tree, 2 * index + 2, size);
}

void inOrder(int tree[], int index, int size) {
    if (index >= size || tree[index] == -1) return;
    inOrder(tree, 2 * index + 1, size);
    printf("%d ", tree[index]);
    inOrder(tree, 2 * index + 2, size);
}

void postOrder(int tree[], int index, int size) {
    if (index >= size || tree[index] == -1) return;
    postOrder(tree, 2 * index + 1, size);
    postOrder(tree, 2 * index + 2, size);
    printf("%d ", tree[index]);
}

int getLeftChild(int tree[], int parentIndex, int size) {
    int leftIndex = 2 * parentIndex + 1;
    if (leftIndex < size && tree[leftIndex] != -1) {
        return tree[leftIndex];
    }
    return -1;
}

int getRightChild(int tree[], int parentIndex, int size) {
    int rightIndex = 2 * parentIndex + 2;
    if (rightIndex < size && tree[rightIndex] != -1) {
        return tree[rightIndex];
    }
    return -1;
}

int main() {
    int tree[MAX_SIZE] = {-1};
    int size = 7;
    tree[0] = 1;
    tree[1] = 2;
    tree[2] = 3;
    tree[3] = 4;
    tree[4] = 5;

    displayTree(tree, size);

    printf("\nPre-order Traversal: ");
    preOrder(tree, 0, size);
    printf("\nIn-order Traversal: ");
    inOrder(tree, 0, size);
    printf("\nPost-order Traversal: ");
    postOrder(tree, 0, size);

    int leftChild = getLeftChild(tree, 0, size);
    int rightChild = getRightChild(tree, 0, size);
    printf("\n\nLeft child of root: %d", leftChild);
    printf("\nRight child of root: %d", rightChild);

    return 0;
}
