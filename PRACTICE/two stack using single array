#include <stdio.h>
#include <stdlib.h>

#define MAX 10

struct TwoStacks {
    int arr[MAX];
    int top1;
    int top2;
};

void initStack(struct TwoStacks* ts) {
    ts->top1 = -1;
    ts->top2 = MAX;
}

void push1(struct TwoStacks* ts, int data) {
    if (ts->top1 < ts->top2 - 1) {
        ts->arr[++ts->top1] = data;
    } else {
        printf("Stack Overflow\n");
    }
}

void push2(struct TwoStacks* ts, int data) {
    if (ts->top1 < ts->top2 - 1) {
        ts->arr[--ts->top2] = data;
    } else {
        printf("Stack Overflow\n");
    }
}

int pop1(struct TwoStacks* ts) {
    if (ts->top1 >= 0) {
        return ts->arr[ts->top1--];
    } else {
        printf("Stack Underflow\n");
        return -1;
    }
}

int pop2(struct TwoStacks* ts) {
    if (ts->top2 < MAX) {
        return ts->arr[ts->top2++];
    } else {
        printf("Stack Underflow\n");
        return -1;
    }
}

int main() {
    struct TwoStacks ts;
    initStack(&ts);

    push1(&ts, 5);
    push1(&ts, 10);
    push2(&ts, 15);
    push2(&ts, 20);

    printf("Popped from Stack 1: %d\n", pop1(&ts));
    printf("Popped from Stack 2: %d\n", pop2(&ts));

    return 0;
}
