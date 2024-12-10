#include <stdio.h>
#include <stdlib.h>

typedef struct Term {
    int coeff;
    int xPower;
    int yPower;
} Term;

typedef struct Node {
    Term term;
    struct Node* next;
} Node;

typedef struct Polynomial {
    Node* head;
} Polynomial;

Term createTerm(int coeff, int xPower, int yPower) {
    Term newTerm;
    newTerm.coeff = coeff;
    newTerm.xPower = xPower;
    newTerm.yPower = yPower;
    return newTerm;
}

Node* createNode(Term term) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->term = term;
    newNode->next = NULL;
    return newNode;
}

Polynomial* createPolynomial() {
    Polynomial* poly = (Polynomial*)malloc(sizeof(Polynomial));
    poly->head = NULL;
    return poly;
}

void addTerm(Polynomial* poly, Term term) {
    Node* newNode = createNode(term);
    if (!poly->head) {
        poly->head = newNode;
    } else {
        Node* current = poly->head;
        while (current->next) {
            current = current->next;
        }
        current->next = newNode;
    }
}

Polynomial* addPolynomials(Polynomial* p1, Polynomial* p2) {
    Polynomial* result = createPolynomial();
    Node* current1 = p1->head;
    Node* current2 = p2->head;

    while (current1 || current2) {
        if (current1 && current2) {
            if (current1->term.xPower == current2->term.xPower &&
                current1->term.yPower == current2->term.yPower) {
                int coeffSum = current1->term.coeff + current2->term.coeff;
                if (coeffSum != 0) {
                    addTerm(result, createTerm(coeffSum, current1->term.xPower, current1->term.yPower));
                }
                current1 = current1->next;
                current2 = current2->next;
            } else if (!current2 || (current1->term.xPower > current2->term.xPower) ||
                       (current1->term.xPower == current2->term.xPower && current1->term.yPower > current2->term.yPower)) {
                addTerm(result, current1->term);
                current1 = current1->next;
            } else {
                addTerm(result, current2->term);
                current2 = current2->next;
            }
        } else if (current1) {
            addTerm(result, current1->term);
            current1 = current1->next;
        } else {
            addTerm(result, current2->term);
            current2 = current2->next;
        }
    }

    return result;
}

void displayPolynomial(Polynomial* poly) {
    if (!poly->head) {
        printf("0\n");
        return;
    }

    Node* current = poly->head;
    while (current) {
        if (current->term.coeff > 0 && current != poly->head) {
            printf("+ ");
        }
        printf("%dx^%dy^%d ", current->term.coeff, current->term.xPower, current->term.yPower);
        current = current->next;
    }
    printf("\n");
}

int main() {
    Polynomial* poly1 = createPolynomial();
    Polynomial* poly2 = createPolynomial();

    addTerm(poly1, createTerm(3, 2, 1));
    addTerm(poly1, createTerm(4, 1, 0));
    addTerm(poly1, createTerm(2, 0, 2));

    addTerm(poly2, createTerm(5, 2, 1));
    addTerm(poly2, createTerm(-4, 1, 0));
    addTerm(poly2, createTerm(1, 0, 1));

    printf("Polynomial 1: ");
    displayPolynomial(poly1);

    printf("Polynomial 2: ");
    displayPolynomial(poly2);

    Polynomial* result = addPolynomials(poly1, poly2);
    printf("Result of Addition: ");
    displayPolynomial(result);

    return 0;
}
