# 100-Days-Of-Code-590027963

1)

a) #include <stdio.h>

int main() {
    int arr[100] = {1, 2, 3, 4, 5};
    int n = 5;
    int pos, element;
    
    printf("Original array: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    
    printf("\nEnter position to insert (0 to %d): ", n);
    scanf("%d", &pos);
    printf("Enter element to insert: ");
    scanf("%d", &element);
    
    // Shift elements to right
    for(int i = n; i > pos; i--) {
        arr[i] = arr[i-1];
    }
    arr[pos] = element;
    n++;
    
    printf("Array after insertion: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    
    return 0;
}

b)
int* twoSum(int* nums, int numsSize, int target, int* returnSize) {
    int* result = (int*)malloc(2 * sizeof(int));
    *returnSize = 2;
    
    for(int i = 0; i < numsSize - 1; i++) {
        for(int j = i + 1; j < numsSize; j++) {
            if(nums[i] + nums[j] == target) {
                result[0] = i;
                result[1] = j;
                return result;
            }
        }
    }
    return result;
}


2)

a) #include <stdio.h>

int main() {
    int arr[100] = {10, 20, 30, 40, 50};
    int n = 5;
    int pos;
    
    printf("Original array: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    
    printf("\nEnter position to delete (0 to %d): ", n-1);
    scanf("%d", &pos);
    
    // Shift elements to left
    for(int i = pos; i < n - 1; i++) {
        arr[i] = arr[i+1];
    }
    n--;
    
    printf("Array after deletion: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    
    return 0;
}

b) int maxProfit(int* prices, int pricesSize) {
    if(pricesSize == 0) return 0;
    
    int minPrice = prices[0];
    int maxProfit = 0;
    
    for(int i = 1; i < pricesSize; i++) {
        if(prices[i] < minPrice) {
            minPrice = prices[i];
        } else {
            int profit = prices[i] - minPrice;
            if(profit > maxProfit) {
                maxProfit = profit;
            }
        }
    }
    
    return maxProfit;
}

3) 

a)



#include <stdio.h>

int main() {
    int arr[100], n, key, comparisons = 0, found = -1;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("Enter element to search: ");
    scanf("%d", &key);
    
    for(int i = 0; i < n; i++) {
        comparisons++;
        if(arr[i] == key) {
            found = i;
            break;
        }
    }
    
    if(found != -1) {
        printf("Element found at index %d\n", found);
    } else {
        printf("Element not found\n");
    }
    printf("Total comparisons: %d\n", comparisons);
    
    return 0;
}

b) int missingNumber(int* arr, int n) {
    int total = (n + 1) * (n + 2) / 2;
    int sum = 0;
    for(int i = 0; i < n; i++) {
        sum += arr[i];
    }
    return total - sum;
}

4) 

a)


#include <stdio.h>

int main() {
    int arr[100], n, temp;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    int left = 0, right = n - 1;
    while(left < right) {
        temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
        left++;
        right--;
    }
    
    printf("Reversed array: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    
    return 0;
}

b) int removeElement(int* nums, int numsSize, int val) {
    int k = 0;
    for(int i = 0; i < numsSize; i++) {
        if(nums[i] != val) {
            nums[k] = nums[i];
            k++;
        }
    }
    return k;
}

5) 

a) #include <stdio.h>
#include <string.h>

typedef struct {
    char timestamp[20];
    char action[10];
} Log;

int main() {
    Log logs[100];
    int n;
    
    printf("Enter number of logs: ");
    scanf("%d", &n);
    
    for(int i = 0; i < n; i++) {
        printf("Log %d (timestamp action): ", i+1);
        scanf("%s %s", logs[i].timestamp, logs[i].action);
    }
    for(int i = 0; i < n - 1; i++) {
        for(int j = 0; j < n - i - 1; j++) {
            if(strcmp(logs[j].timestamp, logs[j+1].timestamp) > 0) {
                Log temp = logs[j];
                logs[j] = logs[j+1];
                logs[j+1] = temp;
            }
        }
    }
    
    printf("\nSorted logs:\n");
    for(int i = 0; i < n; i++) {
        printf("%s %s\n", logs[i].timestamp, logs[i].action);
    }
    
    return 0;
}

b) void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n) {
    int i = m - 1;
    int j = n - 1;
    int k = m + n - 1;
    
    while(i >= 0 && j >= 0) {
        if(nums1[i] > nums2[j]) {
            nums1[k--] = nums1[i--];
        } else {
            nums1[k--] = nums2[j--];
        }
    }
    
    while(j >= 0) {
        nums1[k--] = nums2[j--];
    }
}

6)

a) #include <stdio.h>

int main() {
    int arr[100], n;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d sorted elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    int j = 0;
    for(int i = 0; i < n; i++) {
        if(arr[i] != arr[j]) {
            j++;
            arr[j] = arr[i];
        }
    }
    n = j + 1;
    
    printf("Array after removing duplicates: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    
    return 0;
}

b) void moveZeroes(int* nums, int numsSize) {
    int nonZeroIndex = 0;
    
    for(int i = 0; i < numsSize; i++) {
        if(nums[i] != 0) {
            nums[nonZeroIndex++] = nums[i];
        }
    }
    
    while(nonZeroIndex < numsSize) {
        nums[nonZeroIndex++] = 0;
    }
}

7)

a) #include <stdio.h>

int fibonacci(int n) {
    if(n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    int n;
    printf("Enter n: ");
    scanf("%d", &n);
    
    printf("Fibonacci(%d) = %d\n", n, fibonacci(n));
    
    printf("Fibonacci series: ");
    for(int i = 0; i <= n; i++) {
        printf("%d ", fibonacci(i));
    }
    
    return 0;
}

b) int fib(int n) {
    if(n <= 1) return n;
    
    int prev2 = 0, prev1 = 1, curr;
    for(int i = 2; i <= n; i++) {
        curr = prev1 + prev2;
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1;
}

8)

a) #include <stdio.h>
#include <string.h>

void reverseRecursive(char str[], int start, int end) {
    if(start >= end) {
        return;
    }
    
    // Swap characters
    char temp = str[start];
    str[start] = str[end];
    str[end] = temp;
    
    // Recursive call
    reverseRecursive(str, start + 1, end - 1);
}

int main() {
    char str[100];
    
    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';  // Remove newline
    
    reverseRecursive(str, 0, strlen(str) - 1);
    
    printf("Reversed string: %s\n", str);
    
    return 0;
}

b) void reverseString(char* s, int sSize) {
    int left = 0, right = sSize - 1;
    
    while(left < right) {
        char temp = s[left];
        s[left] = s[right];
        s[right] = temp;
        left++;
        right--;
    }
}

9)

a) #include <stdio.h>
#include <string.h>
#include <ctype.h>

int isPalindromeRecursive(char str[], int start, int end) {
    // Base case: single character or empty
    if(start >= end) {
        return 1;
    }
    
    // Skip non-alphanumeric characters
    while(start < end && !isalnum(str[start])) {
        start++;
    }
    while(start < end && !isalnum(str[end])) {
        end--;
    }
    
    if(tolower(str[start]) != tolower(str[end])) {
        return 0;
    }
    
    return isPalindromeRecursive(str, start + 1, end - 1);
}

int main() {
    char str[100];
    
    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';
    
    if(isPalindromeRecursive(str, 0, strlen(str) - 1)) {
        printf("'%s' is a palindrome\n", str);
    } else {
        printf("'%s' is not a palindrome\n", str);
    }
    
    return 0;

b) #include <ctype.h>
#include <stdbool.h>

bool isPalindrome(char* s) {
    int left = 0;
    int right = strlen(s) - 1;
    
    while(left < right) {
        // Skip non-alphanumeric characters
        while(left < right && !isalnum(s[left])) {
            left++;
        }
        while(left < right && !isalnum(s[right])) {
            right--;
        }
        
        if(tolower(s[left]) != tolower(s[right])) {
            return false;
        }
        
        left++;
        right--;
    }
    
    return true;
}

10) 

a) #include <stdio.h>

double power(double base, int exponent) {
    // Base case
    if(exponent == 0) {
        return 1;
    }
    
    // Handle negative exponent
    if(exponent < 0) {
        return 1 / power(base, -exponent);
    }
    
    // Optimized recursive power (exponentiation by squaring)
    if(exponent % 2 == 0) {
        double half = power(base, exponent / 2);
        return half * half;
    } else {
        return base * power(base, exponent - 1);
    }
}

int main() {
    double base;
    int exponent;
    
    printf("Enter base: ");
    scanf("%lf", &base);
    printf("Enter exponent: ");
    scanf("%d", &exponent);
    
    double result = power(base, exponent);
    printf("%.2lf ^ %d = %.4lf\n", base, exponent, result);
    
    return 0;
}

b) double myPow(double x, int n) {
    // Handle base case
    if(n == 0) {
        return 1.0;
    }
    
    // Handle negative exponent
    if(n < 0) {
        // Special case for INT_MIN to avoid overflow
        if(n == -2147483648) {
            return 1.0 / (myPow(x, 2147483647) * x);
        }
        return 1.0 / myPow(x, -n);
    }
    
    // Exponentiation by squaring
    if(n % 2 == 0) {
        double half = myPow(x, n / 2);
        return half * half;
    } else {
        return x * myPow(x, n - 1);
    }
}

11) 

a) #include <stdio.h>

void towerOfHanoi(int n, char from, char to, char aux) {
    if(n == 1) {
        printf("Move disk 1 from %c to %c\n", from, to);
        return;
    }
    
    towerOfHanoi(n - 1, from, aux, to);
    printf("Move disk %d from %c to %c\n", n, from, to);
    towerOfHanoi(n - 1, aux, to, from);
}

int main() {
    int n;
    printf("Enter number of disks: ");
    scanf("%d", &n);
    
    printf("Steps to solve Tower of Hanoi with %d disks:\n", n);
    towerOfHanoi(n, 'A', 'C', 'B');
    
    printf("Total moves: %d\n", (1 << n) - 1);  // 2^n - 1
    
    return 0;
}

b) // GeeksforGeeks style solution
long long toh(int n, int from, int to, int aux) {
    if(n == 1) {
        printf("move disk 1 from rod %d to rod %d\n", from, to);
        return 1;
    }
    
    long long moves = 0;
    moves += toh(n - 1, from, aux, to);
    printf("move disk %d from rod %d to rod %d\n", n, from, to);
    moves++;
    moves += toh(n - 1, aux, to, from);
    
    return moves;
}

12)

a) #include <stdio.h>

int main() {
    int matrix[100][100], n, symmetric = 1;
    
    printf("Enter size of matrix: ");
    scanf("%d", &n);
    
    printf("Enter matrix elements:\n");
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }
    
    for(int i = 0; i < n && symmetric; i++) {
        for(int j = i + 1; j < n; j++) {
            if(matrix[i][j] != matrix[j][i]) {
                symmetric = 0;
                break;
            }
        }
    }
    
    if(symmetric) {
        printf("Matrix is symmetric\n");
    } else {
        printf("Matrix is not symmetric\n");
    }
    
    return 0;
}

b) bool isToeplitzMatrix(int** matrix, int matrixSize, int* matrixColSize) {
    for(int i = 0; i < matrixSize - 1; i++) {
        for(int j = 0; j < *matrixColSize - 1; j++) {
            if(matrix[i][j] != matrix[i+1][j+1]) {
                return false;
            }
        }
    }
    return true;
}

13)

a) #include <stdio.h>

int main() {
    int matrix[100][100], n;
    
    printf("Enter size of matrix: ");
    scanf("%d", &n);
    
    printf("Enter matrix elements:\n");
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }
    
    int top = 0, bottom = n - 1, left = 0, right = n - 1;
    
    printf("Spiral order: ");
    while(top <= bottom && left <= right) {
        for(int i = left; i <= right; i++) {
            printf("%d ", matrix[top][i]);
        }
        top++;
        
        for(int i = top; i <= bottom; i++) {
            printf("%d ", matrix[i][right]);
        }
        right--;
        
        if(top <= bottom) {
            for(int i = right; i >= left; i--) {
                printf("%d ", matrix[bottom][i]);
            }
            bottom--;
        }
        
        if(left <= right) {
            for(int i = bottom; i >= top; i--) {
                printf("%d ", matrix[i][left]);
            }
            left++;
        }
    }
    
    return 0;
}

b) /**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* spiralOrder(int** matrix, int matrixSize, int* matrixColSize, int* returnSize) {
    if(matrixSize == 0) {
        *returnSize = 0;
        return NULL;
    }
    
    int m = matrixSize, n = *matrixColSize;
    int* result = (int*)malloc(m * n * sizeof(int));
    *returnSize = 0;
    
    int top = 0, bottom = m - 1, left = 0, right = n - 1;
    
    while(top <= bottom && left <= right) {
        for(int i = left; i <= right; i++) {
            result[(*returnSize)++] = matrix[top][i];
        }
        top++;
        
        for(int i = top; i <= bottom; i++) {
            result[(*returnSize)++] = matrix[i][right];
        }
        right--;
        
        if(top <= bottom) {
            for(int i = right; i >= left; i--) {
                result[(*returnSize)++] = matrix[bottom][i];
            }
            bottom--;
        }
        
        if(left <= right) {
            for(int i = bottom; i >= top; i--) {
                result[(*returnSize)++] = matrix[i][left];
            }
            left++;
        }
    }
    
    return result;
}

14)

a) #include <stdio.h>

void rotateMatrix(int matrix[][100], int n) {
    // Step 1: Transpose the matrix
    for(int i = 0; i < n; i++) {
        for(int j = i + 1; j < n; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }
    
    // Step 2: Reverse each row
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n / 2; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[i][n - 1 - j];
            matrix[i][n - 1 - j] = temp;
        }
    }
}

void printMatrix(int matrix[][100], int n) {
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
}

int main() {
    int matrix[100][100], n;
    
    printf("Enter size of matrix: ");
    scanf("%d", &n);
    
    printf("Enter matrix elements:\n");
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }
    
    printf("\nOriginal Matrix:\n");
    printMatrix(matrix, n);
    
    rotateMatrix(matrix, n);
    
    printf("\nMatrix after 90° rotation:\n");
    printMatrix(matrix, n);
    
    return 0;
}

b) void rotate(int** matrix, int matrixSize, int* matrixColSize) {
    int n = matrixSize;
    
    // Step 1: Transpose
    for(int i = 0; i < n; i++) {
        for(int j = i + 1; j < n; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }
    
    // Step 2: Reverse each row
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n / 2; j++) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[i][n - 1 - j];
            matrix[i][n - 1 - j] = temp;
        }
    }
}

15)

a) #include <stdio.h>

int main() {
    int matrix[100][100], n, sum = 0;
    
    printf("Enter size of square matrix: ");
    scanf("%d", &n);
    
    printf("Enter matrix elements:\n");
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }
    
    for(int i = 0; i < n; i++) {
        sum += matrix[i][i];  // Primary diagonal
        if(i != n - 1 - i) {   // Avoid double counting center
            sum += matrix[i][n - 1 - i];  // Secondary diagonal
        }
    }
    
    printf("Sum of diagonals: %d\n", sum);
    
    return 0;
}

b) void setZeroes(int** matrix, int matrixSize, int* matrixColSize) {
    int m = matrixSize, n = *matrixColSize;
    int firstRowZero = 0, firstColZero = 0;
    
    for(int j = 0; j < n; j++) {
        if(matrix[0][j] == 0) firstRowZero = 1;
    }
    
    for(int i = 0; i < m; i++) {
        if(matrix[i][0] == 0) firstColZero = 1;
    }
    
    for(int i = 1; i < m; i++) {
        for(int j = 1; j < n; j++) {
            if(matrix[i][j] == 0) {
                matrix[i][0] = 0;
                matrix[0][j] = 0;
            }
        }
    }
    
    for(int i = 1; i < m; i++) {
        for(int j = 1; j < n; j++) {
            if(matrix[i][0] == 0 || matrix[0][j] == 0) {
                matrix[i][j] = 0;
            }
        }
    }
    
    if(firstRowZero) {
        for(int j = 0; j < n; j++) matrix[0][j] = 0;
    }
    
    if(firstColZero) {
        for(int i = 0; i < m; i++) matrix[i][0] = 0;
    }
}

16)

a) #include <stdio.h>
#include <limits.h>

int maxSumSubarrayOfSizeK(int arr[], int n, int k) {
    if(n < k) {
        printf("Invalid: Array size is smaller than k\n");
        return -1;
    }
    
    // Calculate sum of first window
    int windowSum = 0;
    for(int i = 0; i < k; i++) {
        windowSum += arr[i];
    }
    
    int maxSum = windowSum;
    
    // Slide the window
    for(int i = k; i < n; i++) {
        windowSum = windowSum - arr[i - k] + arr[i];
        if(windowSum > maxSum) {
            maxSum = windowSum;
        }
    }
    
    return maxSum;
}

int main() {
    int arr[100], n, k;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("Enter subarray size (k): ");
    scanf("%d", &k);
    
    int result = maxSumSubarrayOfSizeK(arr, n, k);
    printf("Maximum sum of subarray of size %d is: %d\n", k, result);
    
    return 0;
}

b) double findMaxAverage(int* nums, int numsSize, int k) {
    // Calculate sum of first window
    int windowSum = 0;
    for(int i = 0; i < k; i++) {
        windowSum += nums[i];
    }
    
    int maxSum = windowSum;
    
    // Slide the window
    for(int i = k; i < numsSize; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];
        if(windowSum > maxSum) {
            maxSum = windowSum;
        }
    }
    
    return (double)maxSum / k;
}

17)

a) #include <stdio.h>
#include <limits.h>

void findMinMax(int arr[], int n, int *min, int *max) {
    *min = INT_MAX;
    *max = INT_MIN;
    
    for(int i = 0; i < n; i++) {
        if(arr[i] < *min) {
            *min = arr[i];
        }
        if(arr[i] > *max) {
            *max = arr[i];
        }
    }
}

// Divide and Conquer approach for finding min and max (more efficient)
void findMinMaxDC(int arr[], int left, int right, int *min, int *max) {
    // Single element
    if(left == right) {
        *min = *max = arr[left];
        return;
    }
    
    // Two elements
    if(right == left + 1) {
        if(arr[left] < arr[right]) {
            *min = arr[left];
            *max = arr[right];
        } else {
            *min = arr[right];
            *max = arr[left];
        }
        return;
    }
    
    // More than two elements - divide and conquer
    int mid = (left + right) / 2;
    int min1, max1, min2, max2;
    
    findMinMaxDC(arr, left, mid, &min1, &max1);
    findMinMaxDC(arr, mid + 1, right, &min2, &max2);
    
    *min = (min1 < min2) ? min1 : min2;
    *max = (max1 > max2) ? max1 : max2;
}

int main() {
    int arr[100], n, min, max;
    int choice;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("\nChoose method:\n");
    printf("1. Linear Scan\n");
    printf("2. Divide and Conquer\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    if(choice == 1) {
        findMinMax(arr, n, &min, &max);
        printf("\n--- Linear Scan Result ---\n");
    } else {
        findMinMaxDC(arr, 0, n - 1, &min, &max);
        printf("\n--- Divide and Conquer Result ---\n");
    }
    
    printf("Minimum element: %d\n", min);
    printf("Maximum element: %d\n", max);
    
    return 0;
}

b) #include <stdio.h>
#include <limits.h>

// Approach 1: Kadane's Algorithm (Optimal - O(n) time, O(1) space)
int maxSubArray(int* nums, int numsSize) {
    if(numsSize == 0) return 0;
    
    int currentSum = nums[0];
    int maxSum = nums[0];
    
    for(int i = 1; i < numsSize; i++) {
        // Either extend existing subarray or start new subarray
        if(currentSum + nums[i] > nums[i]) {
            currentSum = currentSum + nums[i];
        } else {
            currentSum = nums[i];
        }
        
        // Update global maximum
        if(currentSum > maxSum) {
            maxSum = currentSum;
        }
    }
    
    return maxSum;
}

// Approach 2: Kadane's Algorithm with tracking subarray indices
int maxSubArrayWithIndices(int* nums, int numsSize, int* start, int* end) {
    if(numsSize == 0) return 0;
    
    int currentSum = nums[0];
    int maxSum = nums[0];
    *start = 0;
    *end = 0;
    int tempStart = 0;
    
    for(int i = 1; i < numsSize; i++) {
        if(currentSum + nums[i] > nums[i]) {
            currentSum = currentSum + nums[i];
        } else {
            currentSum = nums[i];
            tempStart = i;
        }
        
        if(currentSum > maxSum) {
            maxSum = currentSum;
            *start = tempStart;
            *end = i;
        }
    }
    
    return maxSum;
}

// Approach 3: Divide and Conquer (O(n log n))
int crossSum(int* nums, int left, int mid, int right) {
    int leftSum = INT_MIN;
    int sum = 0;
    
    for(int i = mid; i >= left; i--) {
        sum += nums[i];
        if(sum > leftSum) {
            leftSum = sum;
        }
    }
    
    int rightSum = INT_MIN;
    sum = 0;
    
    for(int i = mid + 1; i <= right; i++) {
        sum += nums[i];
        if(sum > rightSum) {
            rightSum = sum;
        }
    }
    
    return leftSum + rightSum;
}

int maxSubArrayDC(int* nums, int left, int right) {
    if(left == right) {
        return nums[left];
    }
    
    int mid = (left + right) / 2;
    
    int leftMax = maxSubArrayDC(nums, left, mid);
    int rightMax = maxSubArrayDC(nums, mid + 1, right);
    int crossMax = crossSum(nums, left, mid, right);
    
    // Return maximum of three
    if(leftMax >= rightMax && leftMax >= crossMax) return leftMax;
    if(rightMax >= leftMax && rightMax >= crossMax) return rightMax;
    return crossMax;
}

// Main function with all approaches
int main() {
    int nums[100], n;
    int choice;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &nums[i]);
    }
    
    printf("\nChoose approach:\n");
    printf("1. Kadane's Algorithm (O(n))\n");
    printf("2. Kadane's Algorithm with Indices\n");
    printf("3. Divide and Conquer (O(n log n))\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    switch(choice) {
        case 1: {
            int result = maxSubArray(nums, n);
            printf("\nMaximum subarray sum: %d\n", result);
            break;
        }
        case 2: {
            int start, end;
            int result = maxSubArrayWithIndices(nums, n, &start, &end);
            printf("\nMaximum subarray sum: %d\n", result);
            printf("Subarray indices: [%d, %d]\n", start, end);
            printf("Subarray elements: ");
            for(int i = start; i <= end; i++) {
                printf("%d ", nums[i]);
            }
            printf("\n");
            break;
        }
        case 3: {
            int result = maxSubArrayDC(nums, 0, n - 1);
            printf("\nMaximum subarray sum: %d\n", result);
            break;
        }
        default:
            printf("Invalid choice\n");
    }
    
    return 0;
}

18)

a) #include <stdio.h>
#include <limits.h>

// Approach 1: Recursive solution
int maxSumNonAdjacentRecursive(int arr[], int n, int index) {
    if(index >= n) {
        return 0;
    }
    
    // Either take current element and skip next
    int take = arr[index] + maxSumNonAdjacentRecursive(arr, n, index + 2);
    
    // Or skip current element
    int skip = maxSumNonAdjacentRecursive(arr, n, index + 1);
    
    return (take > skip) ? take : skip;
}

// Approach 2: Dynamic Programming (Tabulation)
int maxSumNonAdjacentDP(int arr[], int n) {
    if(n == 0) return 0;
    if(n == 1) return arr[0];
    
    int dp[100];
    dp[0] = arr[0];
    dp[1] = (arr[0] > arr[1]) ? arr[0] : arr[1];
    
    for(int i = 2; i < n; i++) {
        int include = arr[i] + dp[i - 2];
        int exclude = dp[i - 1];
        dp[i] = (include > exclude) ? include : exclude;
    }
    
    return dp[n - 1];
}

// Approach 3: Space Optimized DP (O(1) space)
int maxSumNonAdjacentOptimized(int arr[], int n) {
    if(n == 0) return 0;
    if(n == 1) return arr[0];
    
    int prev2 = arr[0];           // dp[i-2]
    int prev1 = (arr[0] > arr[1]) ? arr[0] : arr[1];  // dp[i-1]
    int current;
    
    for(int i = 2; i < n; i++) {
        current = (arr[i] + prev2 > prev1) ? arr[i] + prev2 : prev1;
        prev2 = prev1;
        prev1 = current;
    }
    
    return prev1;
}

// Print the selected elements (using DP with tracking)
int maxSumWithTracking(int arr[], int n, int selected[]) {
    if(n == 0) return 0;
    if(n == 1) {
        selected[0] = arr[0];
        return arr[0];
    }
    
    int dp[100], choice[100];
    dp[0] = arr[0];
    choice[0] = 1;
    
    if(arr[0] > arr[1]) {
        dp[1] = arr[0];
        choice[1] = 0;  // Skipped index 1
    } else {
        dp[1] = arr[1];
        choice[1] = 1;  // Took index 1
    }
    
    for(int i = 2; i < n; i++) {
        int include = arr[i] + dp[i - 2];
        int exclude = dp[i - 1];
        
        if(include > exclude) {
            dp[i] = include;
            choice[i] = 1;  // Took current
        } else {
            dp[i] = exclude;
            choice[i] = 0;  // Skipped current
        }
    }
    
    // Backtrack to find selected elements
    int idx = 0;
    for(int i = n - 1; i >= 0; i--) {
        if(choice[i] == 1) {
            selected[idx++] = arr[i];
            i--;  // Skip adjacent
        }
    }
    
    return dp[n - 1];
}

int main() {
    int arr[100], n, choice;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("\nChoose method:\n");
    printf("1. Recursive\n");
    printf("2. Dynamic Programming (Tabulation)\n");
    printf("3. Space Optimized DP\n");
    printf("4. With element tracking\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    printf("\nArray: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    switch(choice) {
        case 1: {
            int result = maxSumNonAdjacentRecursive(arr, n, 0);
            printf("Maximum sum (non-adjacent): %d\n", result);
            break;
        }
        case 2: {
            int result = maxSumNonAdjacentDP(arr, n);
            printf("Maximum sum (non-adjacent): %d\n", result);
            break;
        }
        case 3: {
            int result = maxSumNonAdjacentOptimized(arr, n);
            printf("Maximum sum (non-adjacent): %d\n", result);
            break;
        }
        case 4: {
            int selected[100] = {0};
            int result = maxSumWithTracking(arr, n, selected);
            printf("Maximum sum (non-adjacent): %d\n", result);
            printf("Selected elements: ");
            for(int i = 0; i < n && selected[i] != 0; i++) {
                printf("%d ", selected[i]);
            }
            printf("\n");
            break;
        }
        default:
            printf("Invalid choice\n");
    }
    
    return 0;
}

b) #include <stdio.h>
#include <stdlib.h>

// Approach 1: Standard DP (O(n) time, O(n) space)
int rob1(int* nums, int numsSize) {
    if(numsSize == 0) return 0;
    if(numsSize == 1) return nums[0];
    
    int* dp = (int*)malloc(numsSize * sizeof(int));
    dp[0] = nums[0];
    dp[1] = (nums[0] > nums[1]) ? nums[0] : nums[1];
    
    for(int i = 2; i < numsSize; i++) {
        int robCurrent = nums[i] + dp[i - 2];
        int skipCurrent = dp[i - 1];
        dp[i] = (robCurrent > skipCurrent) ? robCurrent : skipCurrent;
    }
    
    int result = dp[numsSize - 1];
    free(dp);
    return result;
}

// Approach 2: Space Optimized DP (O(n) time, O(1) space)
int rob2(int* nums, int numsSize) {
    if(numsSize == 0) return 0;
    if(numsSize == 1) return nums[0];
    
    int prev2 = nums[0];                    // dp[i-2]
    int prev1 = (nums[0] > nums[1]) ? nums[0] : nums[1];  // dp[i-1]
    
    for(int i = 2; i < numsSize; i++) {
        int current = (nums[i] + prev2 > prev1) ? nums[i] + prev2 : prev1;
        prev2 = prev1;
        prev1 = current;
    }
    
    return prev1;
}

// Approach 3: Recursive with Memoization (Top-down DP)
int solve(int* nums, int numsSize, int index, int* memo) {
    if(index >= numsSize) return 0;
    if(memo[index] != -1) return memo[index];
    
    int robCurrent = nums[index] + solve(nums, numsSize, index + 2, memo);
    int skipCurrent = solve(nums, numsSize, index + 1, memo);
    
    memo[index] = (robCurrent > skipCurrent) ? robCurrent : skipCurrent;
    return memo[index];
}

int rob3(int* nums, int numsSize) {
    int* memo = (int*)malloc(numsSize * sizeof(int));
    for(int i = 0; i < numsSize; i++) {
        memo[i] = -1;
    }
    int result = solve(nums, numsSize, 0, memo);
    free(memo);
    return result;
}

// Main LeetCode submission function (most efficient)
int rob(int* nums, int numsSize) {
    if(numsSize == 0) return 0;
    if(numsSize == 1) return nums[0];
    
    int prev2 = nums[0];
    int prev1 = (nums[0] > nums[1]) ? nums[0] : nums[1];
    
    for(int i = 2; i < numsSize; i++) {
        int current = prev2 + nums[i];
        if(current < prev1) {
            current = prev1;
        }
        prev2 = prev1;
        prev1 = current;
    }
    
    return prev1;
}

// Test function
int main() {
    int nums[100], n;
    int choice;
    
    printf("Enter number of houses: ");
    scanf("%d", &n);
    
    printf("Enter money in each house: ");
    for(int i = 0; i < n; i++) {
        scanf("%d", &nums[i]);
    }
    
    printf("\nChoose approach:\n");
    printf("1. Standard DP (O(n) space)\n");
    printf("2. Space Optimized DP (O(1) space)\n");
    printf("3. Recursive with Memoization\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    int result;
    switch(choice) {
        case 1:
            result = rob1(nums, n);
            break;
        case 2:
            result = rob2(nums, n);
            break;
        case 3:
            result = rob3(nums, n);
            break;
        default:
            result = rob(nums, n);
    }
    
    printf("\nMaximum amount that can be robbed: %d\n", result);
    
    return 0;
}

19)

a) #include <stdio.h>
#include <stdlib.h>
#include <limits.h>

int main() {
    int arr[100], n;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    // Sort the array (bubble sort)
    for(int i = 0; i < n - 1; i++) {
        for(int j = 0; j < n - i - 1; j++) {
            if(arr[j] > arr[j+1]) {
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
    
    int left = 0, right = n - 1;
    int closestSum = arr[left] + arr[right];
    int pairLeft = left, pairRight = right;
    
    while(left < right) {
        int sum = arr[left] + arr[right];
        
        if(abs(sum) < abs(closestSum)) {
            closestSum = sum;
            pairLeft = left;
            pairRight = right;
        }
        
        if(sum < 0) {
            left++;
        } else {
            right--;
        }
    }
    
    printf("Pair closest to zero: (%d, %d)\n", arr[pairLeft], arr[pairRight]);
    
    return 0;
}

b) int maxSubarraySumCircular(int* nums, int numsSize) {
    int total = 0;
    int currentMax = nums[0], maxSum = nums[0];
    int currentMin = nums[0], minSum = nums[0];
    
    for(int i = 0; i < numsSize; i++) {
        total += nums[i];
        
        if(i > 0) {
            currentMax = (currentMax + nums[i] > nums[i]) ? currentMax + nums[i] : nums[i];
            maxSum = (currentMax > maxSum) ? currentMax : maxSum;
            
            currentMin = (currentMin + nums[i] < nums[i]) ? currentMin + nums[i] : nums[i];
            minSum = (currentMin < minSum) ? currentMin : minSum;
        }
    }
    
    if(maxSum < 0) return maxSum;
    return (maxSum > total - minSum) ? maxSum : total - minSum;

20)

a) #include <stdio.h>

int main() {
    int arr[100], n, count = 0;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    for(int i = 0; i < n; i++) {
        int sum = 0;
        for(int j = i; j < n; j++) {
            sum += arr[j];
            if(sum == 0) {
                count++;
            }
        }
    }
    
    printf("Number of subarrays with sum zero: %d\n", count);
    
    return 0;
}

b) /**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *returnColumnSizes array.
 */
int compare(const void* a, const void* b) {
    return *(int*)a - *(int*)b;
}

int** threeSum(int* nums, int numsSize, int* returnSize, int** returnColumnSizes) {
    if(numsSize < 3) {
        *returnSize = 0;
        return NULL;
    }
    
    qsort(nums, numsSize, sizeof(int), compare);
    
    int** result = (int**)malloc(numsSize * numsSize * sizeof(int*));
    *returnColumnSizes = (int*)malloc(numsSize * numsSize * sizeof(int));
    *returnSize = 0;
    
    for(int i = 0; i < numsSize - 2; i++) {
        if(i > 0 && nums[i] == nums[i-1]) continue;
        
        int left = i + 1, right = numsSize - 1;
        
        while(left < right) {
            int sum = nums[i] + nums[left] + nums[right];
            
            if(sum == 0) {
                result[*returnSize] = (int*)malloc(3 * sizeof(int));
                result[*returnSize][0] = nums[i];
                result[*returnSize][1] = nums[left];
                result[*returnSize][2] = nums[right];
                (*returnColumnSizes)[*returnSize] = 3;
                (*returnSize)++;
                
                while(left < right && nums[left] == nums[left+1]) left++;
                while(left < right && nums[right] == nums[right-1]) right--;
                left++;
                right--;
            } else if(sum < 0) {
                left++;
            } else {
                right--;
            }
        }
    }
    
    return result;
}

21)

a) #include <stdio.h>

void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int partition(int arr[], int low, int high) {
    int pivot = arr[high];  // Choose last element as pivot
    int i = low - 1;         // Index of smaller element
    
    for(int j = low; j < high; j++) {
        // If current element is smaller than or equal to pivot
        if(arr[j] <= pivot) {
            i++;
            swap(&arr[i], &arr[j]);
        }
    }
    swap(&arr[i + 1], &arr[high]);
    return i + 1;
}

// Randomized partition for better performance
int randomPartition(int arr[], int low, int high) {
    int random = low + rand() % (high - low + 1);
    swap(&arr[random], &arr[high]);
    return partition(arr, low, high);
}

void quickSort(int arr[], int low, int high) {
    if(low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[100], n;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("Original array: ");
    printArray(arr, n);
    
    quickSort(arr, 0, n - 1);
    
    printf("Sorted array: ");
    printArray(arr, n);
    
    return 0;
}

b) // Quick Sort implementation for LeetCode
void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int partition(int* nums, int low, int high) {
    int pivot = nums[high];
    int i = low - 1;
    
    for(int j = low; j < high; j++) {
        if(nums[j] <= pivot) {
            i++;
            swap(&nums[i], &nums[j]);
        }
    }
    swap(&nums[i + 1], &nums[high]);
    return i + 1;
}

void quickSort(int* nums, int low, int high) {
    if(low < high) {
        int pi = partition(nums, low, high);
        quickSort(nums, low, pi - 1);
        quickSort(nums, pi + 1, high);
    }
}

int* sortArray(int* nums, int numsSize, int* returnSize) {
    *returnSize = numsSize;
    quickSort(nums, 0, numsSize - 1);
    return nums;
}

22)

a) #include <stdio.h>
#include <stdlib.h>

void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;
    
    // Create temporary arrays
    int* L = (int*)malloc(n1 * sizeof(int));
    int* R = (int*)malloc(n2 * sizeof(int));
    
    // Copy data to temp arrays
    for(int i = 0; i < n1; i++) {
        L[i] = arr[left + i];
    }
    for(int j = 0; j < n2; j++) {
        R[j] = arr[mid + 1 + j];
    }
    
    // Merge the temp arrays back
    int i = 0, j = 0, k = left;
    while(i < n1 && j < n2) {
        if(L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }
    
    // Copy remaining elements
    while(i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }
    while(j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
    
    free(L);
    free(R);
}

void mergeSort(int arr[], int left, int right) {
    if(left < right) {
        int mid = left + (right - left) / 2;
        
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

// Count inversions using merge sort
long long mergeAndCount(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;
    
    int* L = (int*)malloc(n1 * sizeof(int));
    int* R = (int*)malloc(n2 * sizeof(int));
    
    for(int i = 0; i < n1; i++) L[i] = arr[left + i];
    for(int j = 0; j < n2; j++) R[j] = arr[mid + 1 + j];
    
    long long inversions = 0;
    int i = 0, j = 0, k = left;
    
    while(i < n1 && j < n2) {
        if(L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        } else {
            arr[k] = R[j];
            inversions += (n1 - i);
            j++;
        }
        k++;
    }
    
    while(i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }
    while(j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
    
    free(L);
    free(R);
    return inversions;
}

long long countInversions(int arr[], int left, int right) {
    long long inversions = 0;
    if(left < right) {
        int mid = left + (right - left) / 2;
        inversions += countInversions(arr, left, mid);
        inversions += countInversions(arr, mid + 1, right);
        inversions += mergeAndCount(arr, left, mid, right);
    }
    return inversions;
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[100], n;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("Original array: ");
    printArray(arr, n);
    
    mergeSort(arr, 0, n - 1);
    
    printf("Sorted array: ");
    printArray(arr, n);
    
    // Count inversions (classic problem)
    int arr2[100];
    printf("\nEnter array to count inversions: ");
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr2[i]);
    }
    long long inversions = countInversions(arr2, 0, n - 1);
    printf("Number of inversions: %lld\n", inversions);
    
    return 0;
}

b) void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n) {
    int i = m - 1;
    int j = n - 1;
    int k = m + n - 1;
    
    while(i >= 0 && j >= 0) {
        if(nums1[i] > nums2[j]) {
            nums1[k--] = nums1[i--];
        } else {
            nums1[k--] = nums2[j--];
        }
    }
    
    while(j >= 0) {
        nums1[k--] = nums2[j--];
    }
}

23)

a) #include <stdio.h>
#include <limits.h>

void countingSort(int arr[], int n) {
    // Find range of input
    int max = arr[0], min = arr[0];
    for(int i = 1; i < n; i++) {
        if(arr[i] > max) max = arr[i];
        if(arr[i] < min) min = arr[i];
    }
    
    int range = max - min + 1;
    int* count = (int*)calloc(range, sizeof(int));
    int* output = (int*)malloc(n * sizeof(int));
    
    // Store count of each element
    for(int i = 0; i < n; i++) {
        count[arr[i] - min]++;
    }
    
    // Modify count array to store cumulative positions
    for(int i = 1; i < range; i++) {
        count[i] += count[i - 1];
    }
    
    // Build output array (stable sort)
    for(int i = n - 1; i >= 0; i--) {
        output[count[arr[i] - min] - 1] = arr[i];
        count[arr[i] - min]--;
    }
    
    // Copy back to original array
    for(int i = 0; i < n; i++) {
        arr[i] = output[i];
    }
    
    free(count);
    free(output);
}

// Radix Sort helper - counting sort by digit
void countingSortByDigit(int arr[], int n, int exp) {
    int output[100];
    int count[10] = {0};
    
    // Store count of occurrences
    for(int i = 0; i < n; i++) {
        count[(arr[i] / exp) % 10]++;
    }
    
    // Cumulative count
    for(int i = 1; i < 10; i++) {
        count[i] += count[i - 1];
    }
    
    // Build output array
    for(int i = n - 1; i >= 0; i--) {
        output[count[(arr[i] / exp) % 10] - 1] = arr[i];
        count[(arr[i] / exp) % 10]--;
    }
    
    // Copy back
    for(int i = 0; i < n; i++) {
        arr[i] = output[i];
    }
}

void radixSort(int arr[], int n) {
    int max = arr[0];
    for(int i = 1; i < n; i++) {
        if(arr[i] > max) max = arr[i];
    }
    
    for(int exp = 1; max / exp > 0; exp *= 10) {
        countingSortByDigit(arr, n, exp);
    }
}

void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int arr[100], n, choice;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("\nChoose sorting algorithm:\n");
    printf("1. Counting Sort\n");
    printf("2. Radix Sort\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    printf("Original array: ");
    printArray(arr, n);
    
    if(choice == 1) {
        countingSort(arr, n);
        printf("After Counting Sort: ");
    } else {
        radixSort(arr, n);
        printf("After Radix Sort: ");
    }
    printArray(arr, n);
    
    return 0;
}

b) void sortColors(int* nums, int numsSize) {
    int low = 0, mid = 0, high = numsSize - 1;
    
    while(mid <= high) {
        if(nums[mid] == 0) {
            // Swap with low pointer
            int temp = nums[low];
            nums[low] = nums[mid];
            nums[mid] = temp;
            low++;
            mid++;
        } else if(nums[mid] == 1) {
            mid++;
        } else { // nums[mid] == 2
            // Swap with high pointer
            int temp = nums[mid];
            nums[mid] = nums[high];
            nums[high] = temp;
            high--;
        }
    }
}

24)

a) #include <stdio.h>

// Standard binary search (iterative)
int binarySearch(int arr[], int left, int right, int target) {
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] == target) {
            return mid;
        } else if(arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
}

// Recursive binary search
int binarySearchRecursive(int arr[], int left, int right, int target) {
    if(left > right) return -1;
    
    int mid = left + (right - left) / 2;
    
    if(arr[mid] == target) return mid;
    else if(arr[mid] < target) return binarySearchRecursive(arr, mid + 1, right, target);
    else return binarySearchRecursive(arr, left, mid - 1, target);
}

// Search in rotated sorted array
int searchRotated(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] == target) return mid;
        
        // Left half is sorted
        if(arr[left] <= arr[mid]) {
            if(arr[left] <= target && target < arr[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        // Right half is sorted
        else {
            if(arr[mid] < target && target <= arr[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    return -1;
}

// Find first occurrence
int firstOccurrence(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    int result = -1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] == target) {
            result = mid;
            right = mid - 1;  // Search left for earlier occurrence
        } else if(arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return result;
}

// Find last occurrence
int lastOccurrence(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    int result = -1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] == target) {
            result = mid;
            left = mid + 1;  // Search right for later occurrence
        } else if(arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return result;
}

int main() {
    int arr[100], n, target, choice;
    
    printf("Enter number of elements (sorted array): ");
    scanf("%d", &n);
    
    printf("Enter %d sorted elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("Enter target to search: ");
    scanf("%d", &target);
    
    printf("\nChoose operation:\n");
    printf("1. Standard Binary Search (Iterative)\n");
    printf("2. Standard Binary Search (Recursive)\n");
    printf("3. Search in Rotated Sorted Array\n");
    printf("4. First Occurrence\n");
    printf("5. Last Occurrence\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    int result;
    switch(choice) {
        case 1:
            result = binarySearch(arr, 0, n - 1, target);
            break;
        case 2:
            result = binarySearchRecursive(arr, 0, n - 1, target);
            break;
        case 3: {
            printf("Enter rotated array elements (not necessarily sorted): ");
            for(int i = 0; i < n; i++) {
                scanf("%d", &arr[i]);
            }
            result = searchRotated(arr, n, target);
            break;
        }
        case 4:
            result = firstOccurrence(arr, n, target);
            break;
        case 5:
            result = lastOccurrence(arr, n, target);
            break;
        default:
            result = -1;
    }
    
    if(result != -1) {
        printf("Target found at index: %d\n", result);
    } else {
        printf("Target not found\n");
    }
    
    return 0;
}

b) int search(int* nums, int numsSize, int target) {
    int left = 0, right = numsSize - 1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(nums[mid] == target) {
            return mid;
        }
        
        // Left half is sorted
        if(nums[left] <= nums[mid]) {
            if(nums[left] <= target && target < nums[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        // Right half is sorted
        else {
            if(nums[mid] < target && target <= nums[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    
    return -1;
}

25)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int countOccurrences(struct Node* head, int key) {
    int count = 0;
    struct Node* current = head;
    
    while(current != NULL) {
        if(current->data == key) {
            count++;
        }
        current = current->next;
    }
    
    return count;
}

void insertEnd(struct Node** head, int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    
    if(*head == NULL) {
        *head = newNode;
        return;
    }
    
    struct Node* temp = *head;
    while(temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
}

int main() {
    struct Node* head = NULL;
    int n, key;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        int val;
        scanf("%d", &val);
        insertEnd(&head, val);
    }
    
    printf("Enter element to count: ");
    scanf("%d", &key);
    
    printf("Occurrences: %d\n", countOccurrences(head, key));
    
    return 0;
}

b) /**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode *detectCycle(struct ListNode *head) {
    struct ListNode *slow = head, *fast = head;
    
    while(fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
        
        if(slow == fast) {
            slow = head;
            while(slow != fast) {
                slow = slow->next;
                fast = fast->next;
            }
            return slow;
        }
    }
    
    return NULL;
}

26)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* prev;
    struct Node* next;
};

void insertAtBeginning(struct Node** head, int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->prev = NULL;
    newNode->next = *head;
    
    if(*head != NULL) {
        (*head)->prev = newNode;
    }
    *head = newNode;
}

void insertAtEnd(struct Node** head, int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    
    if(*head == NULL) {
        newNode->prev = NULL;
        *head = newNode;
        return;
    }
    
    struct Node* temp = *head;
    while(temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
    newNode->prev = temp;
}

void forwardTraversal(struct Node* head) {
    struct Node* temp = head;
    printf("Forward: ");
    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

void backwardTraversal(struct Node* head) {
    if(head == NULL) return;
    
    struct Node* temp = head;
    while(temp->next != NULL) {
        temp = temp->next;
    }
    
    printf("Backward: ");
    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->prev;
    }
    printf("\n");
}

int main() {
    struct Node* head = NULL;
    int n, val;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        insertAtEnd(&head, val);
    }
    
    forwardTraversal(head);
    backwardTraversal(head);
    
    return 0;
}

b) typedef struct MyLinkedListNode {
    int val;
    struct MyLinkedListNode* next;
} MyLinkedListNode;

typedef struct {
    MyLinkedListNode* head;
    int size;
} MyLinkedList;

MyLinkedList* myLinkedListCreate() {
    MyLinkedList* obj = (MyLinkedList*)malloc(sizeof(MyLinkedList));
    obj->head = NULL;
    obj->size = 0;
    return obj;
}

int myLinkedListGet(MyLinkedList* obj, int index) {
    if(index < 0 || index >= obj->size) return -1;
    
    MyLinkedListNode* current = obj->head;
    for(int i = 0; i < index; i++) {
        current = current->next;
    }
    return current->val;
}

void myLinkedListAddAtHead(MyLinkedList* obj, int val) {
    MyLinkedListNode* newNode = (MyLinkedListNode*)malloc(sizeof(MyLinkedListNode));
    newNode->val = val;
    newNode->next = obj->head;
    obj->head = newNode;
    obj->size++;
}

void myLinkedListAddAtTail(MyLinkedList* obj, int val) {
    MyLinkedListNode* newNode = (MyLinkedListNode*)malloc(sizeof(MyLinkedListNode));
    newNode->val = val;
    newNode->next = NULL;
    
    if(obj->head == NULL) {
        obj->head = newNode;
    } else {
        MyLinkedListNode* current = obj->head;
        while(current->next != NULL) {
            current = current->next;
        }
        current->next = newNode;
    }
    obj->size++;
}

void myLinkedListAddAtIndex(MyLinkedList* obj, int index, int val) {
    if(index < 0 || index > obj->size) return;
    
    if(index == 0) {
        myLinkedListAddAtHead(obj, val);
        return;
    }
    
    MyLinkedListNode* newNode = (MyLinkedListNode*)malloc(sizeof(MyLinkedListNode));
    newNode->val = val;
    
    MyLinkedListNode* current = obj->head;
    for(int i = 0; i < index - 1; i++) {
        current = current->next;
    }
    newNode->next = current->next;
    current->next = newNode;
    obj->size++;
}

void myLinkedListDeleteAtIndex(MyLinkedList* obj, int index) {
    if(index < 0 || index >= obj->size) return;
    
    if(index == 0) {
        MyLinkedListNode* temp = obj->head;
        obj->head = obj->head->next;
        free(temp);
    } else {
        MyLinkedListNode* current = obj->head;
        for(int i = 0; i < index - 1; i++) {
            current = current->next;
        }
        MyLinkedListNode* temp = current->next;
        current->next = temp->next;
        free(temp);
    }
    obj->size--;
}

void myLinkedListFree(MyLinkedList* obj) {
    while(obj->head != NULL) {
        MyLinkedListNode* temp = obj->head;
        obj->head = obj->head->next;
        free(temp);
    }
    free(obj);
}

27)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int getLength(struct Node* head) {
    int length = 0;
    while(head != NULL) {
        length++;
        head = head->next;
    }
    return length;
}

struct Node* findIntersection(struct Node* head1, struct Node* head2) {
    int len1 = getLength(head1);
    int len2 = getLength(head2);
    int diff;
    
    if(len1 > len2) {
        diff = len1 - len2;
        while(diff--) {
            head1 = head1->next;
        }
    } else {
        diff = len2 - len1;
        while(diff--) {
            head2 = head2->next;
        }
    }
    
    while(head1 != NULL && head2 != NULL) {
        if(head1 == head2) {
            return head1;
        }
        head1 = head1->next;
        head2 = head2->next;
    }
    
    return NULL;
}

int main() {
    // Creating two linked lists that intersect
    // List1: 1 -> 2 -> 3 -> 4 -> 5
    // List2: 6 -> 7 -> 4 -> 5
    struct Node* common = NULL;
    
    struct Node* head1 = (struct Node*)malloc(sizeof(struct Node));
    head1->data = 1;
    head1->next = (struct Node*)malloc(sizeof(struct Node));
    head1->next->data = 2;
    head1->next->next = (struct Node*)malloc(sizeof(struct Node));
    head1->next->next->data = 3;
    head1->next->next->next = (struct Node*)malloc(sizeof(struct Node));
    head1->next->next->next->data = 4;
    common = head1->next->next->next;
    common->next = (struct Node*)malloc(sizeof(struct Node));
    common->next->data = 5;
    common->next->next = NULL;
    
    struct Node* head2 = (struct Node*)malloc(sizeof(struct Node));
    head2->data = 6;
    head2->next = (struct Node*)malloc(sizeof(struct Node));
    head2->next->data = 7;
    head2->next->next = common;
    
    struct Node* intersection = findIntersection(head1, head2);
    
    if(intersection != NULL) {
        printf("Intersection at node with data: %d\n", intersection->data);
    } else {
        printf("No intersection\n");
    }
    
    return 0;
}

b) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

void removeCycle(struct Node* head) {
    struct Node *slow = head, *fast = head;
    
    while(fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
        
        if(slow == fast) {
            slow = head;
            while(slow->next != fast->next) {
                slow = slow->next;
                fast = fast->next;
            }
            fast->next = NULL;
            return;
        }
    }
}

void printList(struct Node* head) {
    while(head != NULL) {
        printf("%d ", head->data);
        head = head->next;
    }
    printf("\n");
}

int main() {
    // Creating a linked list with a cycle
    struct Node* head = (struct Node*)malloc(sizeof(struct Node));
    head->data = 1;
    head->next = (struct Node*)malloc(sizeof(struct Node));
    head->next->data = 2;
    head->next->next = (struct Node*)malloc(sizeof(struct Node));
    head->next->next->data = 3;
    head->next->next->next = (struct Node*)malloc(sizeof(struct Node));
    head->next->next->next->data = 4;
    head->next->next->next->next = head->next; // Cycle: 4 -> 2
    
    removeCycle(head);
    printList(head);
    
    return 0;
}

28)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

void insertAtEnd(struct Node** head, int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    
    if(*head == NULL) {
        *head = newNode;
        newNode->next = *head;
        return;
    }
    
    struct Node* temp = *head;
    while(temp->next != *head) {
        temp = temp->next;
    }
    temp->next = newNode;
    newNode->next = *head;
}

void traverse(struct Node* head) {
    if(head == NULL) {
        printf("List is empty\n");
        return;
    }
    
    struct Node* temp = head;
    printf("Circular List: ");
    do {
        printf("%d ", temp->data);
        temp = temp->next;
    } while(temp != head);
    printf("\n");
}

int main() {
    struct Node* head = NULL;
    int n, val;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        insertAtEnd(&head, val);
    }
    
    traverse(head);
    
    return 0;
}

b) /**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* reverseList(struct ListNode* head) {
    struct ListNode *prev = NULL, *current = head, *next = NULL;
    while(current != NULL) {
        next = current->next;
        current->next = prev;
        prev = current;
        current = next;
    }
    return prev;
}

bool isPalindrome(struct ListNode* head) {
    if(head == NULL || head->next == NULL) return true;
    
    // Find middle
    struct ListNode *slow = head, *fast = head;
    while(fast->next != NULL && fast->next->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
    }
    
    // Reverse second half
    struct ListNode* secondHalf = reverseList(slow->next);
    struct ListNode* firstHalf = head;
    struct ListNode* temp = secondHalf;
    
    // Compare
    while(secondHalf != NULL) {
        if(firstHalf->val != secondHalf->val) {
            return false;
        }
        firstHalf = firstHalf->next;
        secondHalf = secondHalf->next;
    }
    
    // Restore (optional)
    reverseList(temp);
    
    return true;
}

29)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

// Function to create a new node
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

// Insert at end
void insertAtEnd(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    if(*head == NULL) {
        *head = newNode;
        return;
    }
    struct Node* temp = *head;
    while(temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
}

// Approach 1: Iterative reversal
void reverseIterative(struct Node** head) {
    struct Node *prev = NULL, *current = *head, *next = NULL;
    
    while(current != NULL) {
        next = current->next;  // Store next
        current->next = prev;  // Reverse link
        prev = current;        // Move prev forward
        current = next;        // Move current forward
    }
    *head = prev;
}

// Approach 2: Recursive reversal
struct Node* reverseRecursive(struct Node* head) {
    if(head == NULL || head->next == NULL) {
        return head;
    }
    
    struct Node* newHead = reverseRecursive(head->next);
    head->next->next = head;
    head->next = NULL;
    
    return newHead;
}

// Find middle of linked list (slow-fast pointer)
struct Node* findMiddle(struct Node* head) {
    if(head == NULL) return NULL;
    
    struct Node *slow = head, *fast = head;
    
    while(fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
    }
    
    return slow;
}

// Print linked list
void printList(struct Node* head) {
    struct Node* temp = head;
    while(temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

int main() {
    struct Node* head = NULL;
    int n, val, choice;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        insertAtEnd(&head, val);
    }
    
    printf("\nOriginal list: ");
    printList(head);
    
    printf("\nChoose operation:\n");
    printf("1. Reverse Linked List (Iterative)\n");
    printf("2. Reverse Linked List (Recursive)\n");
    printf("3. Find Middle Element\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    switch(choice) {
        case 1:
            reverseIterative(&head);
            printf("\nReversed list (Iterative): ");
            printList(head);
            break;
        case 2:
            head = reverseRecursive(head);
            printf("\nReversed list (Recursive): ");
            printList(head);
            break;
        case 3: {
            struct Node* middle = findMiddle(head);
            if(middle != NULL) {
                printf("\nMiddle element: %d\n", middle->data);
            }
            break;
        }
        default:
            printf("Invalid choice\n");
    }
    
    return 0;
}

b) /**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

// Iterative solution
struct ListNode* reverseList(struct ListNode* head) {
    struct ListNode *prev = NULL, *current = head, *next = NULL;
    
    while(current != NULL) {
        next = current->next;
        current->next = prev;
        prev = current;
        current = next;
    }
    
    return prev;
}

// Recursive solution (alternative)
struct ListNode* reverseListRecursive(struct ListNode* head) {
    if(head == NULL || head->next == NULL) {
        return head;
    }
    
    struct ListNode* newHead = reverseListRecursive(head->next);
    head->next->next = head;
    head->next = NULL;
    
    return newHead;
}

30)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

void insertAtEnd(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    if(*head == NULL) {
        *head = newNode;
        return;
    }
    struct Node* temp = *head;
    while(temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
}

// Approach 1: Two-pass algorithm
void removeNthFromEndTwoPass(struct Node** head, int n) {
    if(*head == NULL) return;
    
    // First pass: find length
    int length = 0;
    struct Node* temp = *head;
    while(temp != NULL) {
        length++;
        temp = temp->next;
    }
    
    // If removing first node
    if(n == length) {
        struct Node* toDelete = *head;
        *head = (*head)->next;
        free(toDelete);
        return;
    }
    
    // Second pass: find node before the one to delete
    int pos = length - n;
    temp = *head;
    for(int i = 1; i < pos; i++) {
        temp = temp->next;
    }
    
    struct Node* toDelete = temp->next;
    temp->next = temp->next->next;
    free(toDelete);
}

// Approach 2: One-pass using two pointers
void removeNthFromEndOnePass(struct Node** head, int n) {
    if(*head == NULL) return;
    
    struct Node *fast = *head, *slow = *head;
    
    // Move fast pointer n steps ahead
    for(int i = 0; i < n; i++) {
        if(fast == NULL) return;
        fast = fast->next;
    }
    
    // If removing first node
    if(fast == NULL) {
        struct Node* toDelete = *head;
        *head = (*head)->next;
        free(toDelete);
        return;
    }
    
    // Move both pointers until fast reaches end
    while(fast->next != NULL) {
        slow = slow->next;
        fast = fast->next;
    }
    
    // Remove the nth node from end
    struct Node* toDelete = slow->next;
    slow->next = slow->next->next;
    free(toDelete);
}

// Delete middle node
void deleteMiddle(struct Node** head) {
    if(*head == NULL || (*head)->next == NULL) {
        // Empty list or single node
        free(*head);
        *head = NULL;
        return;
    }
    
    struct Node *slow = *head, *fast = *head;
    struct Node *prev = NULL;
    
    while(fast != NULL && fast->next != NULL) {
        prev = slow;
        slow = slow->next;
        fast = fast->next->next;
    }
    
    // Delete middle node
    prev->next = slow->next;
    free(slow);
}

void printList(struct Node* head) {
    struct Node* temp = head;
    while(temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

int main() {
    struct Node* head = NULL;
    int n, val, pos;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        insertAtEnd(&head, val);
    }
    
    printf("\nOriginal list: ");
    printList(head);
    
    printf("\nChoose operation:\n");
    printf("1. Remove Nth Node from End (Two Pass)\n");
    printf("2. Remove Nth Node from End (One Pass)\n");
    printf("3. Delete Middle Node\n");
    printf("Enter choice: ");
    scanf("%d", &val);
    
    switch(val) {
        case 1:
            printf("Enter n (from end): ");
            scanf("%d", &pos);
            removeNthFromEndTwoPass(&head, pos);
            printf("\nAfter removing %dth node from end: ", pos);
            printList(head);
            break;
        case 2:
            printf("Enter n (from end): ");
            scanf("%d", &pos);
            removeNthFromEndOnePass(&head, pos);
            printf("\nAfter removing %dth node from end: ", pos);
            printList(head);
            break;
        case 3:
            deleteMiddle(&head);
            printf("\nAfter deleting middle node: ");
            printList(head);
            break;
        default:
            printf("Invalid choice\n");
    }
    
    return 0;
}

b) /**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

struct ListNode* removeNthFromEnd(struct ListNode* head, int n) {
    struct ListNode *fast = head, *slow = head;
    
    // Move fast pointer n steps ahead
    for(int i = 0; i < n; i++) {
        if(fast == NULL) return head;
        fast = fast->next;
    }
    
    // If removing first node
    if(fast == NULL) {
        struct ListNode* newHead = head->next;
        free(head);
        return newHead;
    }
    
    // Move both pointers
    while(fast->next != NULL) {
        slow = slow->next;
        fast = fast->next;
    }
    
    // Remove nth node
    struct ListNode* toDelete = slow->next;
    slow->next = slow->next->next;
    free(toDelete);
    
    return head;
}

31)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

void insertAtEnd(struct Node** head, int data) {
    struct Node* newNode = createNode(data);
    if(*head == NULL) {
        *head = newNode;
        return;
    }
    struct Node* temp = *head;
    while(temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
}

// Approach 1: Iterative merge
struct Node* mergeSortedLists(struct Node* head1, struct Node* head2) {
    // Create a dummy node
    struct Node dummy;
    struct Node* tail = &dummy;
    dummy.next = NULL;
    
    while(head1 != NULL && head2 != NULL) {
        if(head1->data <= head2->data) {
            tail->next = head1;
            head1 = head1->next;
        } else {
            tail->next = head2;
            head2 = head2->next;
        }
        tail = tail->next;
    }
    
    // Attach remaining nodes
    if(head1 != NULL) {
        tail->next = head1;
    } else {
        tail->next = head2;
    }
    
    return dummy.next;
}

// Approach 2: Recursive merge
struct Node* mergeSortedListsRecursive(struct Node* head1, struct Node* head2) {
    if(head1 == NULL) return head2;
    if(head2 == NULL) return head1;
    
    if(head1->data <= head2->data) {
        head1->next = mergeSortedListsRecursive(head1->next, head2);
        return head1;
    } else {
        head2->next = mergeSortedListsRecursive(head1, head2->next);
        return head2;
    }
}

// Add two numbers represented as linked lists (reverse order)
struct Node* addTwoNumbers(struct Node* l1, struct Node* l2) {
    struct Node dummy;
    struct Node* tail = &dummy;
    dummy.next = NULL;
    int carry = 0;
    
    while(l1 != NULL || l2 != NULL || carry) {
        int sum = carry;
        
        if(l1 != NULL) {
            sum += l1->data;
            l1 = l1->next;
        }
        if(l2 != NULL) {
            sum += l2->data;
            l2 = l2->next;
        }
        
        carry = sum / 10;
        tail->next = createNode(sum % 10);
        tail = tail->next;
    }
    
    return dummy.next;
}

void printList(struct Node* head) {
    struct Node* temp = head;
    while(temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

int main() {
    struct Node *head1 = NULL, *head2 = NULL;
    int n1, n2, val, choice;
    
    printf("--- List 1 ---\n");
    printf("Enter number of elements (sorted): ");
    scanf("%d", &n1);
    printf("Enter %d sorted elements: ", n1);
    for(int i = 0; i < n1; i++) {
        scanf("%d", &val);
        insertAtEnd(&head1, val);
    }
    
    printf("\n--- List 2 ---\n");
    printf("Enter number of elements (sorted): ");
    scanf("%d", &n2);
    printf("Enter %d sorted elements: ", n2);
    for(int i = 0; i < n2; i++) {
        scanf("%d", &val);
        insertAtEnd(&head2, val);
    }
    
    printf("\nList 1: ");
    printList(head1);
    printf("List 2: ");
    printList(head2);
    
    printf("\nChoose operation:\n");
    printf("1. Merge Two Sorted Lists (Iterative)\n");
    printf("2. Merge Two Sorted Lists (Recursive)\n");
    printf("3. Add Two Numbers (Reverse Order)\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    switch(choice) {
        case 1: {
            struct Node* merged = mergeSortedLists(head1, head2);
            printf("\nMerged list (Iterative): ");
            printList(merged);
            break;
        }
        case 2: {
            struct Node* merged = mergeSortedListsRecursive(head1, head2);
            printf("\nMerged list (Recursive): ");
            printList(merged);
            break;
        }
        case 3: {
            // For add two numbers, we need lists in reverse order
            // Example: 342 represented as 2->4->3
            struct Node *l1 = NULL, *l2 = NULL;
            printf("\nEnter first number digits in reverse order:\n");
            printf("Number of digits: ");
            int d1;
            scanf("%d", &d1);
            printf("Enter digits: ");
            for(int i = 0; i < d1; i++) {
                scanf("%d", &val);
                insertAtEnd(&l1, val);
            }
            
            printf("\nEnter second number digits in reverse order:\n");
            printf("Number of digits: ");
            int d2;
            scanf("%d", &d2);
            printf("Enter digits: ");
            for(int i = 0; i < d2; i++) {
                scanf("%d", &val);
                insertAtEnd(&l2, val);
            }
            
            printf("\nNumber 1: ");
            printList(l1);
            printf("Number 2: ");
            printList(l2);
            
            struct Node* sum = addTwoNumbers(l1, l2);
            printf("Sum: ");
            printList(sum);
            break;
        }
        default:
            printf("Invalid choice\n");
    }
    
    return 0;
}

b) /**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

// Iterative solution
struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2) {
    struct ListNode dummy;
    struct ListNode* tail = &dummy;
    dummy.next = NULL;
    
    while(list1 != NULL && list2 != NULL) {
        if(list1->val <= list2->val) {
            tail->next = list1;
            list1 = list1->next;
        } else {
            tail->next = list2;
            list2 = list2->next;
        }
        tail = tail->next;
    }
    
    tail->next = (list1 != NULL) ? list1 : list2;
    
    return dummy.next;
}

// Recursive solution
struct ListNode* mergeTwoListsRecursive(struct ListNode* list1, struct ListNode* list2) {
    if(list1 == NULL) return list2;
    if(list2 == NULL) return list1;
    
    if(list1->val <= list2->val) {
        list1->next = mergeTwoListsRecursive(list1->next, list2);
        return list1;
    } else {
        list2->next = mergeTwoListsRecursive(list1, list2->next);
        return list2;
    }
}

32)

a)


