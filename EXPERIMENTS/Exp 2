#include <stdio.h>

#define ROWS 2
#define COLS 2

int main() {
    int arr[ROWS][COLS] = { {1, 2}, {3, 4} };

    int i = 1; 
    int j = 1; 

  
    int row_major_addr = (int)&arr[0][0] + (i * COLS + j) * sizeof(int);

    int column_major_addr = (int)&arr[0][0] + (j * ROWS + i) * sizeof(int);

    printf("Row-Major Address of arr[%d][%d]: %d\n", i, j, row_major_addr);
    printf("Column-Major Address of arr[%d][%d]: %d\n", i, j, column_major_addr);

    return 0;
}
