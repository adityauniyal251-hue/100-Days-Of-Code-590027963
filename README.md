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

