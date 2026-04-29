Day 1

#include <stdio.h>

int main() {
    int a, b, sum;

    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);

    sum = a + b;

    printf("Sum = %d", sum);

    return 0;
}

Day 2

#include <stdio.h>

int main() {
    int prices[] = {7, 1, 5, 3, 6, 4};
    int n = 6;
    int minPrice = prices[0];
    int maxProfit = 0;
    int i, profit;

    for(i = 1; i < n; i++) {
        if(prices[i] < minPrice) {
            minPrice = prices[i];
        }

        profit = prices[i] - minPrice;

        if(profit > maxProfit) {
            maxProfit = profit;
        }
    }

    printf("Maximum Profit = %d\n", maxProfit);

    return 0;
}

Day 3

#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 5};
    int n = 5;   // Total numbers should be 1 to 5
    int sum = 0, i;
    int totalSum;
    int missing;

    for(i = 0; i < n - 1; i++) {
        sum += arr[i];
    }

    totalSum = n * (n + 1) / 2;
    missing = totalSum - sum;

    printf("Missing number = %d\n", missing);

    return 0;
}

Day 4

#include <stdio.h>

int main() {
    int arr[100] = {10, 20, 30, 40, 50};
    int n = 5;
    int pos = 3;   // Position to remove (1-based index)
    int i;

    if(pos < 1 || pos > n) {
        printf("Invalid position\n");
    } else {
        for(i = pos - 1; i < n - 1; i++) {
            arr[i] = arr[i + 1];
        }

        n--;

        printf("Array after removing element:\n");
        for(i = 0; i < n; i++) {
            printf("%d ", arr[i]);
        }
    }

    return 0;
}

Day 5

#include <stdio.h>

int main() {
    int nums1[100] = {1, 2, 3, 0, 0, 0};
    int m = 3;
    int nums2[] = {2, 5, 6};
    int n = 3;

    int i = m - 1;
    int j = n - 1;
    int k = m + n - 1;

    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[k] = nums1[i];
            i--;
        } else {
            nums1[k] = nums2[j];
            j--;
        }
        k--;
    }

    while (j >= 0) {
        nums1[k] = nums2[j];
        j--;
        k--;
    }

    printf("Merged Sorted Array:\n");
    for (i = 0; i < m + n; i++) {
        printf("%d ", nums1[i]);
    }

    return 0;
}

Day 6

#include <stdio.h>

int main() {
    int arr[] = {0, 1, 0, 3, 12};
    int n = 5;
    int i, j = 0, temp;

    for(i = 0; i < n; i++) {
        if(arr[i] != 0) {
            temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            j++;
        }
    }

    printf("Array after moving zeroes:\n");
    for(i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}

Day 7

#include <stdio.h>

int main() {
    int n, i;
    int first = 0, second = 1, next;

    printf("Enter number of terms: ");
    scanf("%d", &n);

    printf("Fibonacci Series:\n");

    for(i = 1; i <= n; i++) {
        printf("%d ", first);
        next = first + second;
        first = second;
        second = next;
    }

    return 0;
}

Day 8

#include <stdio.h>

int main() {
    int n;

    printf("Enter a number: ");
    scanf("%d", &n);

    if(n > 0 && (n & (n - 1)) == 0)
        printf("%d is a Power of Two", n);
    else
        printf("%d is NOT a Power of Two", n);

    return 0;
}

Day 9

#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    int i, len;

    printf("Enter a string: ");
    scanf("%s", str);

    len = strlen(str);

    for(i = len - 1; i >= 0; i--) {
        printf("%c", str[i]);
    }

    return 0;
}

Day 10

#include <stdio.h>

int main() {
    int arr1[] = {1, 2, 2, 1};
    int arr2[] = {2, 2};
    int n1 = 4, n2 = 2;
    int i, j;

    printf("Intersection of arrays:\n");

    for(i = 0; i < n1; i++) {
        for(j = 0; j < n2; j++) {
            if(arr1[i] == arr2[j]) {
                printf("%d ", arr1[i]);
                arr2[j] = -1;   // Mark as used
                break;
            }
        }
    }

    return 0;
}

Day 11

#include <stdio.h>

int main() {
    int row = 2, col = 3;
    int matrix[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };

    int i, j;

    printf("Transpose Matrix:\n");

    for(i = 0; i < col; i++) {
        for(j = 0; j < row; j++) {
            printf("%d ", matrix[j][i]);
        }
        printf("\n");
    }

    return 0;
}

Day 12 

#include <stdio.h>

int main() {
    int matrix[3][4] = {
        {1, 2, 3, 4},
        {5, 1, 2, 3},
        {6, 5, 1, 2}
    };

    int rows = 3, cols = 4;
    int i, j, flag = 1;

    for(i = 1; i < rows; i++) {
        for(j = 1; j < cols; j++) {
            if(matrix[i][j] != matrix[i - 1][j - 1]) {
                flag = 0;
                break;
            }
        }
    }

    if(flag)
        printf("Matrix is Toeplitz Matrix");
    else
        printf("Matrix is NOT Toeplitz Matrix");

    return 0;
}

Day 13

#include <stdio.h>

int main() {
    int matrix[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    int top = 0, bottom = 2, left = 0, right = 2;
    int i;

    printf("Spiral Matrix:\n");

    while(top <= bottom && left <= right) {

        for(i = left; i <= right; i++)
            printf("%d ", matrix[top][i]);
        top++;

        for(i = top; i <= bottom; i++)
            printf("%d ", matrix[i][right]);
        right--;

        if(top <= bottom) {
            for(i = right; i >= left; i--)
                printf("%d ", matrix[bottom][i]);
            bottom--;
        }

        if(left <= right) {
            for(i = bottom; i >= top; i--)
                printf("%d ", matrix[i][left]);
            left++;
        }
    }

    return 0;
}

Day 14

#include <stdio.h>

int main() {
    int matrix[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    int top = 0, bottom = 2, left = 0, right = 2;
    int i;

    printf("Spiral Matrix:\n");

    while(top <= bottom && left <= right) {

        for(i = left; i <= right; i++)
            printf("%d ", matrix[top][i]);
        top++;

        for(i = top; i <= bottom; i++)
            printf("%d ", matrix[i][right]);
        right--;

        if(top <= bottom) {
            for(i = right; i >= left; i--)
                printf("%d ", matrix[bottom][i]);
            bottom--;
        }

        if(left <= right) {
            for(i = bottom; i >= top; i--)
                printf("%d ", matrix[i][left]);
            left++;
        }
    }

    return 0;
}

Day 15

#include <stdio.h>

int main() {
    int matrix[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    int n = 3;
    int i, j, temp;

    for(i = 0; i < n; i++) {
        for(j = i + 1; j < n; j++) {
            temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }

    for(i = 0; i < n; i++) {
        for(j = 0; j < n / 2; j++) {
            temp = matrix[i][j];
            matrix[i][j] = matrix[i][n - j - 1];
            matrix[i][n - j - 1] = temp;
        }
    }

    printf("Rotated Image:\n");

    for(i = 0; i < n; i++) {
        for(j = 0; j < n; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }

    return 0;
}

Day 16

#include <stdio.h>

int main() {
    int matrix[3][3] = {
        {1, 1, 1},
        {1, 0, 1},
        {1, 1, 1}
    };

    int rows = 3, cols = 3;
    int row[3] = {0}, col[3] = {0};
    int i, j;

    for(i = 0; i < rows; i++) {
        for(j = 0; j < cols; j++) {
            if(matrix[i][j] == 0) {
                row[i] = 1;
                col[j] = 1;
            }
        }
    }

    for(i = 0; i < rows; i++) {
        for(j = 0; j < cols; j++) {
            if(row[i] == 1 || col[j] == 1) {
                matrix[i][j] = 0;
            }
        }
    }

    printf("Matrix after setting zeroes:\n");

    for(i = 0; i < rows; i++) {
        for(j = 0; j < cols; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }

    return 0;
}

Day 17

#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 4, 5, 6, 7};
    int n = 7;
    int k = 3;
    int temp[7];
    int i;

    for(i = 0; i < n; i++) {
        temp[(i + k) % n] = arr[i];
    }

    for(i = 0; i < n; i++) {
        arr[i] = temp[i];
    }

    printf("Rotated Array:\n");

    for(i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}

Day 18

#include <stdio.h>

int main() {
    int arr[] = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
    int n = 9;
    int i;
    int maxSum = arr[0];
    int currentSum = arr[0];

    for(i = 1; i < n; i++) {
        if(currentSum + arr[i] > arr[i])
            currentSum = currentSum + arr[i];
        else
            currentSum = arr[i];

        if(currentSum > maxSum)
            maxSum = currentSum;
    }

    printf("Maximum Subarray Sum = %d", maxSum);

    return 0;
}

Day 19



