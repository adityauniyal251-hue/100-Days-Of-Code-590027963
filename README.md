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

a) #include <stdio.h>
#include <stdlib.h>
#define MAX 100

struct Stack {
    int arr[MAX];
    int top;
};

void initStack(struct Stack* s) {
    s->top = -1;
}

int isEmpty(struct Stack* s) {
    return s->top == -1;
}

int isFull(struct Stack* s) {
    return s->top == MAX - 1;
}

void push(struct Stack* s, int value) {
    if(isFull(s)) {
        printf("Stack Overflow!\n");
        return;
    }
    s->arr[++(s->top)] = value;
    printf("Pushed %d\n", value);
}

int pop(struct Stack* s) {
    if(isEmpty(s)) {
        printf("Stack Underflow!\n");
        return -1;
    }
    return s->arr[(s->top)--];
}

int peek(struct Stack* s) {
    if(isEmpty(s)) {
        printf("Stack is empty\n");
        return -1;
    }
    return s->arr[s->top];
}

void display(struct Stack* s) {
    if(isEmpty(s)) {
        printf("Stack is empty\n");
        return;
    }
    printf("Stack: ");
    for(int i = 0; i <= s->top; i++) {
        printf("%d ", s->arr[i]);
    }
    printf("\n");
}

int main() {
    struct Stack s;
    initStack(&s);
    
    push(&s, 10);
    push(&s, 20);
    push(&s, 30);
    display(&s);
    
    printf("Popped: %d\n", pop(&s));
    printf("Top element: %d\n", peek(&s));
    display(&s);
    
    return 0;
}

b) typedef struct {
    int* stack;
    int* minStack;
    int top;
} MinStack;

MinStack* minStackCreate() {
    MinStack* obj = (MinStack*)malloc(sizeof(MinStack));
    obj->stack = (int*)malloc(10000 * sizeof(int));
    obj->minStack = (int*)malloc(10000 * sizeof(int));
    obj->top = -1;
    return obj;
}

void minStackPush(MinStack* obj, int val) {
    obj->top++;
    obj->stack[obj->top] = val;
    
    if(obj->top == 0) {
        obj->minStack[obj->top] = val;
    } else {
        obj->minStack[obj->top] = (val < obj->minStack[obj->top - 1]) ? 
                                   val : obj->minStack[obj->top - 1];
    }
}

void minStackPop(MinStack* obj) {
    if(obj->top >= 0) {
        obj->top--;
    }
}

int minStackTop(MinStack* obj) {
    return obj->stack[obj->top];
}

int minStackGetMin(MinStack* obj) {
    return obj->minStack[obj->top];
}

void minStackFree(MinStack* obj) {
    free(obj->stack);
    free(obj->minStack);
    free(obj);
}

33)

a) #include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define MAX 100

struct Stack {
    char arr[MAX];
    int top;
};

void initStack(struct Stack* s) {
    s->top = -1;
}

int isEmpty(struct Stack* s) {
    return s->top == -1;
}

int isFull(struct Stack* s) {
    return s->top == MAX - 1;
}

void push(struct Stack* s, char ch) {
    if(!isFull(s)) {
        s->arr[++(s->top)] = ch;
    }
}

char pop(struct Stack* s) {
    if(!isEmpty(s)) {
        return s->arr[(s->top)--];
    }
    return '\0';
}

char peek(struct Stack* s) {
    if(!isEmpty(s)) {
        return s->arr[s->top];
    }
    return '\0';
}

// Function to return precedence of operators
int precedence(char op) {
    switch(op) {
        case '+':
        case '-':
            return 1;
        case '*':
        case '/':
            return 2;
        case '^':
            return 3;
        default:
            return 0;
    }
}

// Check if character is an operator
int isOperator(char ch) {
    return (ch == '+' || ch == '-' || ch == '*' || ch == '/' || ch == '^');
}

// Convert infix expression to postfix
void infixToPostfix(char* infix, char* postfix) {
    struct Stack s;
    initStack(&s);
    int i = 0, j = 0;
    
    while(infix[i] != '\0') {
        char ch = infix[i];
        
        // If operand, add to output
        if(isalnum(ch)) {
            postfix[j++] = ch;
        }
        // If '(', push to stack
        else if(ch == '(') {
            push(&s, ch);
        }
        // If ')', pop until '('
        else if(ch == ')') {
            while(!isEmpty(&s) && peek(&s) != '(') {
                postfix[j++] = pop(&s);
            }
            pop(&s);  // Remove '('
        }
        // If operator
        else if(isOperator(ch)) {
            while(!isEmpty(&s) && precedence(peek(&s)) >= precedence(ch) && peek(&s) != '(') {
                postfix[j++] = pop(&s);
            }
            push(&s, ch);
        }
        i++;
    }
    
    // Pop remaining operators
    while(!isEmpty(&s)) {
        postfix[j++] = pop(&s);
    }
    postfix[j] = '\0';
}

// Evaluate postfix expression
int evaluatePostfix(char* postfix) {
    struct Stack s;
    initStack(&s);
    int i = 0;
    
    while(postfix[i] != '\0') {
        char ch = postfix[i];
        
        if(isdigit(ch)) {
            push(&s, ch - '0');  // Convert char to int
        }
        else if(isOperator(ch)) {
            int b = pop(&s);
            int a = pop(&s);
            int result;
            
            switch(ch) {
                case '+': result = a + b; break;
                case '-': result = a - b; break;
                case '*': result = a * b; break;
                case '/': result = a / b; break;
                case '^': 
                    result = 1;
                    for(int j = 0; j < b; j++) result *= a;
                    break;
                default: result = 0;
            }
            push(&s, result);
        }
        i++;
    }
    
    return pop(&s);
}

int main() {
    char infix[MAX], postfix[MAX];
    int choice;
    
    printf("Choose operation:\n");
    printf("1. Infix to Postfix Conversion\n");
    printf("2. Evaluate Postfix Expression\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    getchar();  // Consume newline
    
    if(choice == 1) {
        printf("Enter infix expression: ");
        fgets(infix, MAX, stdin);
        infix[strcspn(infix, "\n")] = '\0';
        
        infixToPostfix(infix, postfix);
        printf("Postfix expression: %s\n", postfix);
    }
    else if(choice == 2) {
        printf("Enter postfix expression (single digits): ");
        fgets(postfix, MAX, stdin);
        postfix[strcspn(postfix, "\n")] = '\0';
        
        int result = evaluatePostfix(postfix);
        printf("Result: %d\n", result);
    }
    
    return 0;
}

b) #include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

// Stack implementation
typedef struct {
    int* arr;
    int top;
    int capacity;
} Stack;

Stack* createStack(int capacity) {
    Stack* s = (Stack*)malloc(sizeof(Stack));
    s->arr = (int*)malloc(capacity * sizeof(int));
    s->top = -1;
    s->capacity = capacity;
    return s;
}

void push(Stack* s, int val) {
    if(s->top < s->capacity - 1) {
        s->arr[++(s->top)] = val;
    }
}

int pop(Stack* s) {
    if(s->top >= 0) {
        return s->arr[(s->top)--];
    }
    return 0;
}

int evalRPN(char** tokens, int tokensSize) {
    Stack* s = createStack(tokensSize);
    
    for(int i = 0; i < tokensSize; i++) {
        char* token = tokens[i];
        
        // Check if token is an operator
        if(strlen(token) == 1 && (token[0] == '+' || token[0] == '-' || 
           token[0] == '*' || token[0] == '/')) {
            int b = pop(s);
            int a = pop(s);
            int result;
            
            switch(token[0]) {
                case '+': result = a + b; break;
                case '-': result = a - b; break;
                case '*': result = a * b; break;
                case '/': result = a / b; break;
                default: result = 0;
            }
            push(s, result);
        } else {
            // Token is a number
            push(s, atoi(token));
        }
    }
    
    int answer = pop(s);
    free(s->arr);
    free(s);
    return answer;
}

// Test function
int main() {
    char* tokens1[] = {"2", "1", "+", "3", "*"};
    int size1 = 5;
    printf("Test 1: 2 1 + 3 * = %d\n", evalRPN(tokens1, size1));  // (2+1)*3 = 9
    
    char* tokens2[] = {"4", "13", "5", "/", "+"};
    int size2 = 5;
    printf("Test 2: 4 13 5 / + = %d\n", evalRPN(tokens2, size2));  // 4 + (13/5) = 6
    
    char* tokens3[] = {"10", "6", "9", "3", "+", "-11", "*", "/", "*", "17", "+", "5", "+"};
    int size3 = 13;
    printf("Test 3: %d\n", evalRPN(tokens3, size3));
    
    return 0;
}

34)

a) #include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

#define MAX 100

struct Stack {
    char arr[MAX];
    int top;
};

void initStack(struct Stack* s) {
    s->top = -1;
}

int isEmpty(struct Stack* s) {
    return s->top == -1;
}

void push(struct Stack* s, char ch) {
    if(s->top < MAX - 1) {
        s->arr[++(s->top)] = ch;
    }
}

char pop(struct Stack* s) {
    if(!isEmpty(s)) {
        return s->arr[(s->top)--];
    }
    return '\0';
}

char peek(struct Stack* s) {
    if(!isEmpty(s)) {
        return s->arr[s->top];
    }
    return '\0';
}

int precedence(char op) {
    switch(op) {
        case '+': case '-': return 1;
        case '*': case '/': return 2;
        case '^': return 3;
        default: return 0;
    }
}

int isOperator(char ch) {
    return (ch == '+' || ch == '-' || ch == '*' || ch == '/' || ch == '^');
}

void reverseString(char* str) {
    int n = strlen(str);
    for(int i = 0; i < n / 2; i++) {
        char temp = str[i];
        str[i] = str[n - 1 - i];
        str[n - 1 - i] = temp;
    }
}

void replaceBrackets(char* str) {
    for(int i = 0; str[i] != '\0'; i++) {
        if(str[i] == '(') str[i] = ')';
        else if(str[i] == ')') str[i] = '(';
    }
}

void infixToPrefix(char* infix, char* prefix) {
    // Step 1: Reverse the infix expression
    char reversed[MAX];
    strcpy(reversed, infix);
    reverseString(reversed);
    
    // Step 2: Replace brackets
    replaceBrackets(reversed);
    
    // Step 3: Convert to postfix using the same algorithm
    struct Stack s;
    initStack(&s);
    char postfix[MAX];
    int i = 0, j = 0;
    
    while(reversed[i] != '\0') {
        char ch = reversed[i];
        
        if(isalnum(ch)) {
            postfix[j++] = ch;
        }
        else if(ch == '(') {
            push(&s, ch);
        }
        else if(ch == ')') {
            while(!isEmpty(&s) && peek(&s) != '(') {
                postfix[j++] = pop(&s);
            }
            pop(&s);
        }
        else if(isOperator(ch)) {
            while(!isEmpty(&s) && precedence(peek(&s)) > precedence(ch)) {
                postfix[j++] = pop(&s);
            }
            push(&s, ch);
        }
        i++;
    }
    
    while(!isEmpty(&s)) {
        postfix[j++] = pop(&s);
    }
    postfix[j] = '\0';
    
    // Step 4: Reverse to get prefix
    strcpy(prefix, postfix);
    reverseString(prefix);
}

int main() {
    char infix[MAX], prefix[MAX];
    
    printf("Enter infix expression: ");
    fgets(infix, MAX, stdin);
    infix[strcspn(infix, "\n")] = '\0';
    
    infixToPrefix(infix, prefix);
    printf("Prefix expression: %s\n", prefix);
    
    return 0;
}

b) #include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

int calculate(char* s) {
    int stack[10000];
    int top = -1;
    int currentNum = 0;
    int result = 0;
    int sign = 1;  // 1 for positive, -1 for negative
    
    for(int i = 0; s[i] != '\0'; i++) {
        char ch = s[i];
        
        if(isdigit(ch)) {
            currentNum = currentNum * 10 + (ch - '0');
        }
        else if(ch == '+' || ch == '-') {
            result += sign * currentNum;
            currentNum = 0;
            sign = (ch == '+') ? 1 : -1;
        }
        else if(ch == '(') {
            // Push result and sign to stack
            stack[++top] = result;
            stack[++top] = sign;
            // Reset for new expression
            result = 0;
            sign = 1;
        }
        else if(ch == ')') {
            result += sign * currentNum;
            currentNum = 0;
            // Pop sign and previous result
            int prevSign = stack[top--];
            int prevResult = stack[top--];
            result = prevResult + prevSign * result;
        }
    }
    
    result += sign * currentNum;
    return result;
}

int main() {
    char expr[1000];
    printf("Enter expression (spaces allowed): ");
    fgets(expr, 1000, stdin);
    
    int result = calculate(expr);
    printf("Result: %d\n", result);
    
    return 0;
}

35)

a) #include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>

#define MAX 100

struct Stack {
    char arr[MAX];
    int top;
};

void initStack(struct Stack* s) {
    s->top = -1;
}

bool isEmpty(struct Stack* s) {
    return s->top == -1;
}

bool isFull(struct Stack* s) {
    return s->top == MAX - 1;
}

void push(struct Stack* s, char ch) {
    if(!isFull(s)) {
        s->arr[++(s->top)] = ch;
    }
}

char pop(struct Stack* s) {
    if(!isEmpty(s)) {
        return s->arr[(s->top)--];
    }
    return '\0';
}

char peek(struct Stack* s) {
    if(!isEmpty(s)) {
        return s->arr[s->top];
    }
    return '\0';
}

bool isMatchingPair(char opening, char closing) {
    return (opening == '(' && closing == ')') ||
           (opening == '{' && closing == '}') ||
           (opening == '[' && closing == ']');
}

bool isBalanced(char* expression) {
    struct Stack s;
    initStack(&s);
    
    for(int i = 0; expression[i] != '\0'; i++) {
        char ch = expression[i];
        
        // If opening bracket, push to stack
        if(ch == '(' || ch == '{' || ch == '[') {
            push(&s, ch);
        }
        // If closing bracket, check with stack top
        else if(ch == ')' || ch == '}' || ch == ']') {
            if(isEmpty(&s)) {
                return false;
            }
            char top = pop(&s);
            if(!isMatchingPair(top, ch)) {
                return false;
            }
        }
        // Ignore other characters (optional)
    }
    
    return isEmpty(&s);
}

int main() {
    char expression[MAX];
    
    printf("Enter expression with brackets: ");
    fgets(expression, MAX, stdin);
    expression[strcspn(expression, "\n")] = '\0';
    
    if(isBalanced(expression)) {
        printf("Balanced Parentheses!\n");
    } else {
        printf("Unbalanced Parentheses!\n");
    }
    
    return 0;
}

b) #include <stdbool.h>
#include <string.h>

bool isValid(char* s) {
    char stack[10000];
    int top = -1;
    
    for(int i = 0; s[i] != '\0'; i++) {
        char ch = s[i];
        
        if(ch == '(' || ch == '{' || ch == '[') {
            stack[++top] = ch;
        } else {
            if(top == -1) return false;
            
            char topChar = stack[top--];
            
            if(ch == ')' && topChar != '(') return false;
            if(ch == '}' && topChar != '{') return false;
            if(ch == ']' && topChar != '[') return false;
        }
    }
    
    return top == -1;
}

36)

a) #include <stdio.h>
#include <stdlib.h>

#define MAX 100

struct Stack {
    int arr[MAX];
    int top;
};

void initStack(struct Stack* s) {
    s->top = -1;
}

int isEmpty(struct Stack* s) {
    return s->top == -1;
}

void push(struct Stack* s, int val) {
    if(s->top < MAX - 1) {
        s->arr[++(s->top)] = val;
    }
}

int pop(struct Stack* s) {
    if(!isEmpty(s)) {
        return s->arr[(s->top)--];
    }
    return -1;
}

int peek(struct Stack* s) {
    if(!isEmpty(s)) {
        return s->arr[s->top];
    }
    return -1;
}

// Next Greater Element to the Right
void nextGreaterElement(int arr[], int n) {
    struct Stack s;
    initStack(&s);
    int result[MAX];
    
    // Traverse from right to left
    for(int i = n - 1; i >= 0; i--) {
        // Pop elements smaller than current
        while(!isEmpty(&s) && peek(&s) <= arr[i]) {
            pop(&s);
        }
        
        // If stack is empty, no greater element
        if(isEmpty(&s)) {
            result[i] = -1;
        } else {
            result[i] = peek(&s);
        }
        
        push(&s, arr[i]);
    }
    
    // Print results
    printf("Element -> Next Greater Element\n");
    for(int i = 0; i < n; i++) {
        printf("    %d   ->        %d\n", arr[i], result[i]);
    }
}

// Next Greater Element to the Left
void nextGreaterLeft(int arr[], int n) {
    struct Stack s;
    initStack(&s);
    int result[MAX];
    
    for(int i = 0; i < n; i++) {
        while(!isEmpty(&s) && peek(&s) <= arr[i]) {
            pop(&s);
        }
        
        if(isEmpty(&s)) {
            result[i] = -1;
        } else {
            result[i] = peek(&s);
        }
        
        push(&s, arr[i]);
    }
    
    printf("Element -> Next Greater Left\n");
    for(int i = 0; i < n; i++) {
        printf("    %d   ->        %d\n", arr[i], result[i]);
    }
}

int main() {
    int arr[MAX], n, choice;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("\nChoose operation:\n");
    printf("1. Next Greater Element (Right)\n");
    printf("2. Next Greater Element (Left)\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    if(choice == 1) {
        nextGreaterElement(arr, n);
    } else {
        nextGreaterLeft(arr, n);
    }
    
    return 0;
}

b) /**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* nextGreaterElement(int* nums1, int nums1Size, int* nums2, int nums2Size, int* returnSize) {
    // Stack to find next greater for all elements in nums2
    int stack[10000];
    int top = -1;
    
    // Hash map to store next greater for each value
    int map[10001];  // Assuming values are within range
    for(int i = 0; i < 10001; i++) {
        map[i] = -1;
    }
    
    // Find next greater for all elements in nums2
    for(int i = 0; i < nums2Size; i++) {
        while(top != -1 && stack[top] < nums2[i]) {
            map[stack[top]] = nums2[i];
            top--;
        }
        stack[++top] = nums2[i];
    }
    
    // Prepare result for nums1
    int* result = (int*)malloc(nums1Size * sizeof(int));
    *returnSize = nums1Size;
    
    for(int i = 0; i < nums1Size; i++) {
        result[i] = map[nums1[i]];
    }
    
    return result;
}

37)

a) #include <stdio.h>
#include <stdlib.h>
#include <limits.h>

#define MAX 100

typedef struct {
    int data;
    int priority;
} Element;

typedef struct {
    Element arr[MAX];
    int size;
} PriorityQueue;

// Initialize priority queue
void initQueue(PriorityQueue* pq) {
    pq->size = 0;
}

// Check if queue is empty
int isEmpty(PriorityQueue* pq) {
    return pq->size == 0;
}

// Check if queue is full
int isFull(PriorityQueue* pq) {
    return pq->size == MAX;
}

// Insert element with priority (higher priority number = higher priority)
void enqueue(PriorityQueue* pq, int data, int priority) {
    if(isFull(pq)) {
        printf("Priority Queue is full!\n");
        return;
    }
    
    Element newElement;
    newElement.data = data;
    newElement.priority = priority;
    
    int i = pq->size - 1;
    
    // Shift elements with lower priority to the right
    while(i >= 0 && pq->arr[i].priority < priority) {
        pq->arr[i + 1] = pq->arr[i];
        i--;
    }
    
    pq->arr[i + 1] = newElement;
    pq->size++;
    
    printf("Inserted: %d (Priority: %d)\n", data, priority);
}

// Remove and return highest priority element
int dequeue(PriorityQueue* pq) {
    if(isEmpty(pq)) {
        printf("Priority Queue is empty!\n");
        return -1;
    }
    
    int data = pq->arr[0].data;
    
    // Shift all elements left
    for(int i = 0; i < pq->size - 1; i++) {
        pq->arr[i] = pq->arr[i + 1];
    }
    pq->size--;
    
    return data;
}

// Peek at highest priority element
int peek(PriorityQueue* pq) {
    if(isEmpty(pq)) {
        printf("Priority Queue is empty!\n");
        return -1;
    }
    return pq->arr[0].data;
}

// Display the priority queue
void display(PriorityQueue* pq) {
    if(isEmpty(pq)) {
        printf("Priority Queue is empty\n");
        return;
    }
    
    printf("Priority Queue (Data, Priority): ");
    for(int i = 0; i < pq->size; i++) {
        printf("(%d,%d) ", pq->arr[i].data, pq->arr[i].priority);
    }
    printf("\n");
}

int main() {
    PriorityQueue pq;
    initQueue(&pq);
    int choice, data, priority;
    
    while(1) {
        printf("\n--- Priority Queue Menu ---\n");
        printf("1. Enqueue (Insert)\n");
        printf("2. Dequeue (Remove Highest Priority)\n");
        printf("3. Peek (View Highest Priority)\n");
        printf("4. Display\n");
        printf("5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        
        switch(choice) {
            case 1:
                printf("Enter data: ");
                scanf("%d", &data);
                printf("Enter priority (higher = more important): ");
                scanf("%d", &priority);
                enqueue(&pq, data, priority);
                break;
            case 2:
                data = dequeue(&pq);
                if(data != -1) {
                    printf("Dequeued: %d\n", data);
                }
                break;
            case 3:
                data = peek(&pq);
                if(data != -1) {
                    printf("Highest priority element: %d\n", data);
                }
                break;
            case 4:
                display(&pq);
                break;
            case 5:
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice!\n");
        }
    }
    
    return 0;
}

b) #include <stdio.h>
#include <stdlib.h>

// Min-Heap implementation
typedef struct {
    int* heap;
    int size;
    int capacity;
    int k;
} KthLargest;

// Swap two integers
void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// Heapify down (min-heap property)
void heapifyDown(int* heap, int size, int idx) {
    int smallest = idx;
    int left = 2 * idx + 1;
    int right = 2 * idx + 2;
    
    if(left < size && heap[left] < heap[smallest]) {
        smallest = left;
    }
    if(right < size && heap[right] < heap[smallest]) {
        smallest = right;
    }
    
    if(smallest != idx) {
        swap(&heap[idx], &heap[smallest]);
        heapifyDown(heap, size, smallest);
    }
}

// Heapify up (min-heap property)
void heapifyUp(int* heap, int idx) {
    if(idx == 0) return;
    
    int parent = (idx - 1) / 2;
    
    if(heap[parent] > heap[idx]) {
        swap(&heap[parent], &heap[idx]);
        heapifyUp(heap, parent);
    }
}

// Create KthLargest object
KthLargest* kthLargestCreate(int k, int* nums, int numsSize) {
    KthLargest* obj = (KthLargest*)malloc(sizeof(KthLargest));
    obj->k = k;
    obj->size = 0;
    obj->capacity = k + 10;
    obj->heap = (int*)malloc(obj->capacity * sizeof(int));
    
    // Add all elements
    for(int i = 0; i < numsSize; i++) {
        kthLargestAdd(obj, nums[i]);
    }
    
    return obj;
}

// Add value and return kth largest
int kthLargestAdd(KthLargest* obj, int val) {
    if(obj->size < obj->k) {
        // Heap not full yet, just insert
        obj->heap[obj->size] = val;
        heapifyUp(obj->heap, obj->size);
        obj->size++;
    } else if(val > obj->heap[0]) {
        // Replace root and heapify
        obj->heap[0] = val;
        heapifyDown(obj->heap, obj->size, 0);
    }
    
    return obj->heap[0];
}

// Free memory
void kthLargestFree(KthLargest* obj) {
    free(obj->heap);
    free(obj);
}

// Test the implementation
int main() {
    int nums[] = {4, 5, 8, 2};
    int numsSize = 4;
    int k = 3;
    
    KthLargest* obj = kthLargestCreate(k, nums, numsSize);
    
    printf("Kth largest (k=%d) after adding:\n", k);
    printf("Add 3 -> %d\n", kthLargestAdd(obj, 3));
    printf("Add 5 -> %d\n", kthLargestAdd(obj, 5));
    printf("Add 10 -> %d\n", kthLargestAdd(obj, 10));
    printf("Add 9 -> %d\n", kthLargestAdd(obj, 9));
    printf("Add 4 -> %d\n", kthLargestAdd(obj, 4));
    
    kthLargestFree(obj);
    return 0;
}

38)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 5

typedef struct {
    int arr[MAX];
    int front;
    int rear;
    int size;
} Queue;

// Initialize queue
void initQueue(Queue* q) {
    q->front = 0;
    q->rear = -1;
    q->size = 0;
}

// Check if queue is empty
bool isEmpty(Queue* q) {
    return q->size == 0;
}

// Check if queue is full
bool isFull(Queue* q) {
    return q->size == MAX;
}

// Enqueue (add element to rear)
void enqueue(Queue* q, int val) {
    if(isFull(q)) {
        printf("Queue is full! Cannot enqueue %d\n", val);
        return;
    }
    
    q->rear = (q->rear + 1) % MAX;
    q->arr[q->rear] = val;
    q->size++;
    printf("Enqueued: %d\n", val);
}

// Dequeue (remove element from front)
int dequeue(Queue* q) {
    if(isEmpty(q)) {
        printf("Queue is empty!\n");
        return -1;
    }
    
    int val = q->arr[q->front];
    q->front = (q->front + 1) % MAX;
    q->size--;
    return val;
}

// Peek at front element
int peek(Queue* q) {
    if(isEmpty(q)) {
        printf("Queue is empty!\n");
        return -1;
    }
    return q->arr[q->front];
}

// Display queue
void display(Queue* q) {
    if(isEmpty(q)) {
        printf("Queue is empty\n");
        return;
    }
    
    printf("Queue (front to rear): ");
    for(int i = 0; i < q->size; i++) {
        int idx = (q->front + i) % MAX;
        printf("%d ", q->arr[idx]);
    }
    printf("\n");
}

int main() {
    Queue q;
    initQueue(&q);
    int choice, val;
    
    while(1) {
        printf("\n--- Queue Menu ---\n");
        printf("1. Enqueue\n");
        printf("2. Dequeue\n");
        printf("3. Peek\n");
        printf("4. Display\n");
        printf("5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        
        switch(choice) {
            case 1:
                printf("Enter value: ");
                scanf("%d", &val);
                enqueue(&q, val);
                break;
            case 2:
                val = dequeue(&q);
                if(val != -1) {
                    printf("Dequeued: %d\n", val);
                }
                break;
            case 3:
                val = peek(&q);
                if(val != -1) {
                    printf("Front element: %d\n", val);
                }
                break;
            case 4:
                display(&q);
                break;
            case 5:
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice!\n");
        }
    }
    
    return 0;
}

b) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

typedef struct {
    int* stack1;  // For push operations
    int* stack2;  // For pop/peek operations
    int top1;
    int top2;
    int capacity;
} MyQueue;

MyQueue* myQueueCreate() {
    MyQueue* obj = (MyQueue*)malloc(sizeof(MyQueue));
    obj->capacity = 10000;
    obj->stack1 = (int*)malloc(obj->capacity * sizeof(int));
    obj->stack2 = (int*)malloc(obj->capacity * sizeof(int));
    obj->top1 = -1;
    obj->top2 = -1;
    return obj;
}

void myQueuePush(MyQueue* obj, int x) {
    obj->stack1[++(obj->top1)] = x;
}

int myQueuePop(MyQueue* obj) {
    // If stack2 is empty, transfer all elements from stack1
    if(obj->top2 == -1) {
        while(obj->top1 != -1) {
            obj->stack2[++(obj->top2)] = obj->stack1[(obj->top1)--];
        }
    }
    return obj->stack2[(obj->top2)--];
}

int myQueuePeek(MyQueue* obj) {
    if(obj->top2 == -1) {
        while(obj->top1 != -1) {
            obj->stack2[++(obj->top2)] = obj->stack1[(obj->top1)--];
        }
    }
    return obj->stack2[obj->top2];
}

bool myQueueEmpty(MyQueue* obj) {
    return (obj->top1 == -1 && obj->top2 == -1);
}

void myQueueFree(MyQueue* obj) {
    free(obj->stack1);
    free(obj->stack2);
    free(obj);
}

39)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 100

typedef struct {
    int arr[MAX];
    int front;
    int rear;
    int size;
} Deque;

void initDeque(Deque* dq) {
    dq->front = -1;
    dq->rear = 0;
    dq->size = 0;
}

bool isEmpty(Deque* dq) {
    return dq->size == 0;
}

bool isFull(Deque* dq) {
    return dq->size == MAX;
}

// Insert at front
void insertFront(Deque* dq, int val) {
    if(isFull(dq)) {
        printf("Deque is full!\n");
        return;
    }
    
    if(isEmpty(dq)) {
        dq->front = 0;
        dq->rear = 0;
    } else {
        dq->front = (dq->front - 1 + MAX) % MAX;
    }
    
    dq->arr[dq->front] = val;
    dq->size++;
    printf("Inserted %d at front\n", val);
}

// Insert at rear
void insertRear(Deque* dq, int val) {
    if(isFull(dq)) {
        printf("Deque is full!\n");
        return;
    }
    
    if(isEmpty(dq)) {
        dq->front = 0;
        dq->rear = 0;
    } else {
        dq->rear = (dq->rear + 1) % MAX;
    }
    
    dq->arr[dq->rear] = val;
    dq->size++;
    printf("Inserted %d at rear\n", val);
}

// Delete from front
int deleteFront(Deque* dq) {
    if(isEmpty(dq)) {
        printf("Deque is empty!\n");
        return -1;
    }
    
    int val = dq->arr[dq->front];
    
    if(dq->front == dq->rear) {
        // Only one element
        dq->front = -1;
        dq->rear = -1;
    } else {
        dq->front = (dq->front + 1) % MAX;
    }
    
    dq->size--;
    return val;
}

// Delete from rear
int deleteRear(Deque* dq) {
    if(isEmpty(dq)) {
        printf("Deque is empty!\n");
        return -1;
    }
    
    int val = dq->arr[dq->rear];
    
    if(dq->front == dq->rear) {
        dq->front = -1;
        dq->rear = -1;
    } else {
        dq->rear = (dq->rear - 1 + MAX) % MAX;
    }
    
    dq->size--;
    return val;
}

int getFront(Deque* dq) {
    if(isEmpty(dq)) return -1;
    return dq->arr[dq->front];
}

int getRear(Deque* dq) {
    if(isEmpty(dq)) return -1;
    return dq->arr[dq->rear];
}

void display(Deque* dq) {
    if(isEmpty(dq)) {
        printf("Deque is empty\n");
        return;
    }
    
    printf("Deque (front to rear): ");
    int i = dq->front;
    while(1) {
        printf("%d ", dq->arr[i]);
        if(i == dq->rear) break;
        i = (i + 1) % MAX;
    }
    printf("\n");
}

int main() {
    Deque dq;
    initDeque(&dq);
    int choice, val;
    
    while(1) {
        printf("\n--- Deque Menu ---\n");
        printf("1. Insert Front\n");
        printf("2. Insert Rear\n");
        printf("3. Delete Front\n");
        printf("4. Delete Rear\n");
        printf("5. Get Front\n");
        printf("6. Get Rear\n");
        printf("7. Display\n");
        printf("8. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        
        switch(choice) {
            case 1:
                printf("Enter value: ");
                scanf("%d", &val);
                insertFront(&dq, val);
                break;
            case 2:
                printf("Enter value: ");
                scanf("%d", &val);
                insertRear(&dq, val);
                break;
            case 3:
                val = deleteFront(&dq);
                if(val != -1) printf("Deleted from front: %d\n", val);
                break;
            case 4:
                val = deleteRear(&dq);
                if(val != -1) printf("Deleted from rear: %d\n", val);
                break;
            case 5:
                val = getFront(&dq);
                if(val != -1) printf("Front element: %d\n", val);
                break;
            case 6:
                val = getRear(&dq);
                if(val != -1) printf("Rear element: %d\n", val);
                break;
            case 7:
                display(&dq);
                break;
            case 8:
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice!\n");
        }
    }
    
    return 0;
}

b) typedef struct {
    int* arr;
    int front;
    int rear;
    int size;
    int capacity;
} MyCircularDeque;

MyCircularDeque* myCircularDequeCreate(int k) {
    MyCircularDeque* obj = (MyCircularDeque*)malloc(sizeof(MyCircularDeque));
    obj->arr = (int*)malloc(k * sizeof(int));
    obj->front = -1;
    obj->rear = -1;
    obj->size = 0;
    obj->capacity = k;
    return obj;
}

bool myCircularDequeIsEmpty(MyCircularDeque* obj) {
    return obj->size == 0;
}

bool myCircularDequeIsFull(MyCircularDeque* obj) {
    return obj->size == obj->capacity;
}

bool myCircularDequeInsertFront(MyCircularDeque* obj, int value) {
    if(myCircularDequeIsFull(obj)) return false;
    
    if(myCircularDequeIsEmpty(obj)) {
        obj->front = 0;
        obj->rear = 0;
    } else {
        obj->front = (obj->front - 1 + obj->capacity) % obj->capacity;
    }
    
    obj->arr[obj->front] = value;
    obj->size++;
    return true;
}

bool myCircularDequeInsertLast(MyCircularDeque* obj, int value) {
    if(myCircularDequeIsFull(obj)) return false;
    
    if(myCircularDequeIsEmpty(obj)) {
        obj->front = 0;
        obj->rear = 0;
    } else {
        obj->rear = (obj->rear + 1) % obj->capacity;
    }
    
    obj->arr[obj->rear] = value;
    obj->size++;
    return true;
}

bool myCircularDequeDeleteFront(MyCircularDeque* obj) {
    if(myCircularDequeIsEmpty(obj)) return false;
    
    if(obj->front == obj->rear) {
        obj->front = -1;
        obj->rear = -1;
    } else {
        obj->front = (obj->front + 1) % obj->capacity;
    }
    
    obj->size--;
    return true;
}

bool myCircularDequeDeleteLast(MyCircularDeque* obj) {
    if(myCircularDequeIsEmpty(obj)) return false;
    
    if(obj->front == obj->rear) {
        obj->front = -1;
        obj->rear = -1;
    } else {
        obj->rear = (obj->rear - 1 + obj->capacity) % obj->capacity;
    }
    
    obj->size--;
    return true;
}

int myCircularDequeGetFront(MyCircularDeque* obj) {
    if(myCircularDequeIsEmpty(obj)) return -1;
    return obj->arr[obj->front];
}

int myCircularDequeGetRear(MyCircularDeque* obj) {
    if(myCircularDequeIsEmpty(obj)) return -1;
    return obj->arr[obj->rear];
}

void myCircularDequeFree(MyCircularDeque* obj) {
    free(obj->arr);
    free(obj);
}

40)

a) #include <stdio.h>

// Swap two elements
void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// Heapify a subtree rooted at index i
void heapify(int arr[], int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;
    
    if(left < n && arr[left] > arr[largest]) {
        largest = left;
    }
    if(right < n && arr[right] > arr[largest]) {
        largest = right;
    }
    
    if(largest != i) {
        swap(&arr[i], &arr[largest]);
        heapify(arr, n, largest);
    }
}

// Build max heap and sort
void heapSort(int arr[], int n) {
    // Build max heap (rearrange array)
    for(int i = n / 2 - 1; i >= 0; i--) {
        heapify(arr, n, i);
    }
    
    // Extract elements from heap one by one
    for(int i = n - 1; i > 0; i--) {
        // Move current root to end
        swap(&arr[0], &arr[i]);
        
        // Call heapify on reduced heap
        heapify(arr, i, 0);
    }
}

// Build min heap (for descending order)
void heapifyMin(int arr[], int n, int i) {
    int smallest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;
    
    if(left < n && arr[left] < arr[smallest]) {
        smallest = left;
    }
    if(right < n && arr[right] < arr[smallest]) {
        smallest = right;
    }
    
    if(smallest != i) {
        swap(&arr[i], &arr[smallest]);
        heapifyMin(arr, n, smallest);
    }
}

void heapSortDescending(int arr[], int n) {
    for(int i = n / 2 - 1; i >= 0; i--) {
        heapifyMin(arr, n, i);
    }
    
    for(int i = n - 1; i > 0; i--) {
        swap(&arr[0], &arr[i]);
        heapifyMin(arr, i, 0);
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
    
    printf("\nChoose sorting order:\n");
    printf("1. Ascending (Max Heap)\n");
    printf("2. Descending (Min Heap)\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    printf("Original array: ");
    printArray(arr, n);
    
    if(choice == 1) {
        heapSort(arr, n);
        printf("Sorted ascending: ");
    } else {
        heapSortDescending(arr, n);
        printf("Sorted descending: ");
    }
    printArray(arr, n);
    
    return 0;
}

b) /**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* dailyTemperatures(int* temperatures, int temperaturesSize, int* returnSize) {
    int* result = (int*)malloc(temperaturesSize * sizeof(int));
    *returnSize = temperaturesSize;
    
    int* stack = (int*)malloc(temperaturesSize * sizeof(int));
    int top = -1;
    
    for(int i = 0; i < temperaturesSize; i++) {
        result[i] = 0;
        
        while(top != -1 && temperatures[stack[top]] < temperatures[i]) {
            int idx = stack[top--];
            result[idx] = i - idx;
        }
        stack[++top] = i;
    }
    
    free(stack);
    return result;
}

41)

a) #include <stdio.h>
#include <stdlib.h>
#include <limits.h>

#define MAX 100

typedef struct {
    int heap[MAX];
    int size;
} MinHeap;

void initHeap(MinHeap* h) {
    h->size = 0;
}

int isEmpty(MinHeap* h) {
    return h->size == 0;
}

int isFull(MinHeap* h) {
    return h->size == MAX;
}

// Get parent index
int parent(int i) {
    return (i - 1) / 2;
}

// Get left child index
int leftChild(int i) {
    return 2 * i + 1;
}

// Get right child index
int rightChild(int i) {
    return 2 * i + 2;
}

// Heapify up (for insertion)
void heapifyUp(MinHeap* h, int idx) {
    while(idx > 0 && h->heap[parent(idx)] > h->heap[idx]) {
        int temp = h->heap[parent(idx)];
        h->heap[parent(idx)] = h->heap[idx];
        h->heap[idx] = temp;
        idx = parent(idx);
    }
}

// Heapify down (for deletion)
void heapifyDown(MinHeap* h, int idx) {
    int smallest = idx;
    int left = leftChild(idx);
    int right = rightChild(idx);
    
    if(left < h->size && h->heap[left] < h->heap[smallest]) {
        smallest = left;
    }
    if(right < h->size && h->heap[right] < h->heap[smallest]) {
        smallest = right;
    }
    
    if(smallest != idx) {
        int temp = h->heap[idx];
        h->heap[idx] = h->heap[smallest];
        h->heap[smallest] = temp;
        heapifyDown(h, smallest);
    }
}

// Insert element
void insert(MinHeap* h, int val) {
    if(isFull(h)) {
        printf("Heap is full!\n");
        return;
    }
    
    h->heap[h->size] = val;
    h->size++;
    heapifyUp(h, h->size - 1);
    printf("Inserted %d\n", val);
}

// Extract minimum element
int extractMin(MinHeap* h) {
    if(isEmpty(h)) {
        printf("Heap is empty!\n");
        return INT_MIN;
    }
    
    int min = h->heap[0];
    h->heap[0] = h->heap[h->size - 1];
    h->size--;
    heapifyDown(h, 0);
    
    return min;
}

// Get minimum element without removing
int getMin(MinHeap* h) {
    if(isEmpty(h)) return INT_MIN;
    return h->heap[0];
}

// Display heap
void display(MinHeap* h) {
    if(isEmpty(h)) {
        printf("Heap is empty\n");
        return;
    }
    
    printf("Min Heap: ");
    for(int i = 0; i < h->size; i++) {
        printf("%d ", h->heap[i]);
    }
    printf("\n");
}

int main() {
    MinHeap h;
    initHeap(&h);
    int choice, val;
    
    while(1) {
        printf("\n--- Min Heap Menu ---\n");
        printf("1. Insert\n");
        printf("2. Extract Min\n");
        printf("3. Get Min\n");
        printf("4. Display\n");
        printf("5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        
        switch(choice) {
            case 1:
                printf("Enter value: ");
                scanf("%d", &val);
                insert(&h, val);
                break;
            case 2:
                val = extractMin(&h);
                if(val != INT_MIN) {
                    printf("Extracted min: %d\n", val);
                }
                break;
            case 3:
                val = getMin(&h);
                if(val != INT_MIN) {
                    printf("Minimum element: %d\n", val);
                }
                break;
            case 4:
                display(&h);
                break;
            case 5:
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice!\n");
        }
    }
    
    return 0;
}

b) #include <stdlib.h>

// Min-heap implementation
void heapify(int* heap, int size, int i) {
    int smallest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;
    
    if(left < size && heap[left] < heap[smallest]) smallest = left;
    if(right < size && heap[right] < heap[smallest]) smallest = right;
    
    if(smallest != i) {
        int temp = heap[i];
        heap[i] = heap[smallest];
        heap[smallest] = temp;
        heapify(heap, size, smallest);
    }
}

int findKthLargest(int* nums, int numsSize, int k) {
    // Create min-heap of first k elements
    int* heap = (int*)malloc(k * sizeof(int));
    for(int i = 0; i < k; i++) {
        heap[i] = nums[i];
    }
    
    // Build min-heap
    for(int i = k / 2 - 1; i >= 0; i--) {
        heapify(heap, k, i);
    }
    
    // Process remaining elements
    for(int i = k; i < numsSize; i++) {
        if(nums[i] > heap[0]) {
            heap[0] = nums[i];
            heapify(heap, k, 0);
        }
    }
    
    int result = heap[0];
    free(heap);
    return result;
}

42)

a) #include <stdio.h>
#include <stdlib.h>

#define MAX 1000

typedef struct {
    int value;
    int frequency;
} Element;

int compareFrequency(const void* a, const void* b) {
    return ((Element*)b)->frequency - ((Element*)a)->frequency;
}

void topKFrequent(int arr[], int n, int k) {
    // Assuming values are within a range (0-999)
    int freq[MAX] = {0};
    Element elements[MAX];
    int uniqueCount = 0;
    
    // Count frequencies
    for(int i = 0; i < n; i++) {
        freq[arr[i]]++;
    }
    
    // Store unique elements with their frequencies
    for(int i = 0; i < MAX; i++) {
        if(freq[i] > 0) {
            elements[uniqueCount].value = i;
            elements[uniqueCount].frequency = freq[i];
            uniqueCount++;
        }
    }
    
    // Sort by frequency descending
    qsort(elements, uniqueCount, sizeof(Element), compareFrequency);
    
    // Print top k
    printf("Top %d frequent elements: ", k);
    for(int i = 0; i < k && i < uniqueCount; i++) {
        printf("%d ", elements[i].value);
    }
    printf("\n");
}

int main() {
    int arr[100], n, k;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("Enter k: ");
    scanf("%d", &k);
    
    topKFrequent(arr, n, k);
    
    return 0;
}

b) /**
 * Note: The returned array must be malloced, assume caller calls free().
 */
typedef struct {
    int num;
    int freq;
} Pair;

int compare(const void* a, const void* b) {
    return ((Pair*)b)->freq - ((Pair*)a)->freq;
}

int* topKFrequent(int* nums, int numsSize, int k, int* returnSize) {
    // Find max element to size frequency array
    int max = nums[0];
    for(int i = 1; i < numsSize; i++) {
        if(nums[i] > max) max = nums[i];
    }
    
    int* freq = (int*)calloc(max + 1, sizeof(int));
    for(int i = 0; i < numsSize; i++) {
        freq[nums[i]]++;
    }
    
    Pair* pairs = (Pair*)malloc((max + 1) * sizeof(Pair));
    int pairCount = 0;
    
    for(int i = 0; i <= max; i++) {
        if(freq[i] > 0) {
            pairs[pairCount].num = i;
            pairs[pairCount].freq = freq[i];
            pairCount++;
        }
    }
    
    qsort(pairs, pairCount, sizeof(Pair), compare);
    
    int* result = (int*)malloc(k * sizeof(int));
    *returnSize = k;
    
    for(int i = 0; i < k; i++) {
        result[i] = pairs[i].num;
    }
    
    free(freq);
    free(pairs);
    return result;
}

43) 

a) #include <stdio.h>
#include <stdlib.h>

#define MAX 100

typedef struct {
    int arr[MAX];
    int front;
    int rear;
    int size;
} Deque;

void initDeque(Deque* dq) {
    dq->front = -1;
    dq->rear = -1;
    dq->size = 0;
}

int isEmpty(Deque* dq) {
    return dq->size == 0;
}

void pushBack(Deque* dq, int val) {
    if(isEmpty(dq)) {
        dq->front = 0;
        dq->rear = 0;
    } else {
        dq->rear++;
    }
    dq->arr[dq->rear] = val;
    dq->size++;
}

void popFront(Deque* dq) {
    if(isEmpty(dq)) return;
    
    if(dq->front == dq->rear) {
        dq->front = -1;
        dq->rear = -1;
    } else {
        dq->front++;
    }
    dq->size--;
}

void popBack(Deque* dq) {
    if(isEmpty(dq)) return;
    
    if(dq->front == dq->rear) {
        dq->front = -1;
        dq->rear = -1;
    } else {
        dq->rear--;
    }
    dq->size--;
}

int getFront(Deque* dq) {
    if(isEmpty(dq)) return -1;
    return dq->arr[dq->front];
}

int getBack(Deque* dq) {
    if(isEmpty(dq)) return -1;
    return dq->arr[dq->rear];
}

void slidingWindowMaximum(int arr[], int n, int k) {
    Deque dq;
    initDeque(&dq);
    
    printf("Sliding window maximums:\n");
    
    for(int i = 0; i < n; i++) {
        // Remove elements outside current window
        while(!isEmpty(&dq) && getFront(&dq) <= i - k) {
            popFront(&dq);
        }
        
        // Remove smaller elements from back
        while(!isEmpty(&dq) && arr[getBack(&dq)] <= arr[i]) {
            popBack(&dq);
        }
        
        pushBack(&dq, i);
        
        // Print maximum for windows starting from index k-1
        if(i >= k - 1) {
            printf("Window %d-%d: %d\n", i - k + 1, i, arr[getFront(&dq)]);
        }
    }
}

int main() {
    int arr[100], n, k;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("Enter window size k: ");
    scanf("%d", &k);
    
    slidingWindowMaximum(arr, n, k);
    
    return 0;
}

b) /**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* maxSlidingWindow(int* nums, int numsSize, int k, int* returnSize) {
    if(numsSize == 0 || k == 0) {
        *returnSize = 0;
        return NULL;
    }
    
    int* result = (int*)malloc((numsSize - k + 1) * sizeof(int));
    *returnSize = numsSize - k + 1;
    
    int* deque = (int*)malloc(numsSize * sizeof(int));
    int front = 0, rear = -1;
    int resultIdx = 0;
    
    for(int i = 0; i < numsSize; i++) {
        // Remove elements outside window
        while(front <= rear && deque[front] <= i - k) {
            front++;
        }
        
        // Remove smaller elements
        while(front <= rear && nums[deque[rear]] <= nums[i]) {
            rear--;
        }
        
        deque[++rear] = i;
        
        // Add to result when window is complete
        if(i >= k - 1) {
            result[resultIdx++] = nums[deque[front]];
        }
    }
    
    free(deque);
    return result;
}

44)

a) #include <stdio.h>
#include <stdlib.h>

#define MAX_TASKS 26

int leastInterval(char* tasks, int n, int maxTaskTypes) {
    int freq[MAX_TASKS] = {0};
    int len = 0;
    
    // Count frequency of each task
    for(int i = 0; tasks[i] != '\0'; i++) {
        freq[tasks[i] - 'A']++;
        len++;
    }
    
    // Find max frequency
    int maxFreq = 0;
    for(int i = 0; i < MAX_TASKS; i++) {
        if(freq[i] > maxFreq) {
            maxFreq = freq[i];
        }
    }
    
    // Count how many tasks have max frequency
    int maxCount = 0;
    for(int i = 0; i < MAX_TASKS; i++) {
        if(freq[i] == maxFreq) {
            maxCount++;
        }
    }
    
    // Calculate result
    int result = (maxFreq - 1) * (n + 1) + maxCount;
    return (result > len) ? result : len;
}

int main() {
    char tasks[100];
    int n;
    
    printf("Enter tasks (as uppercase letters without spaces): ");
    scanf("%s", tasks);
    
    printf("Enter cooling period n: ");
    scanf("%d", &n);
    
    int result = leastInterval(tasks, n, 26);
    printf("Least intervals needed: %d\n", result);
    
    return 0;
}

b) #include <stdlib.h>

int leastInterval(char* tasks, int tasksSize, int n) {
    int freq[26] = {0};
    
    for(int i = 0; i < tasksSize; i++) {
        freq[tasks[i] - 'A']++;
    }
    
    // Find max frequency
    int maxFreq = 0;
    for(int i = 0; i < 26; i++) {
        if(freq[i] > maxFreq) {
            maxFreq = freq[i];
        }
    }
    
    // Count tasks with max frequency
    int maxCount = 0;
    for(int i = 0; i < 26; i++) {
        if(freq[i] == maxFreq) {
            maxCount++;
        }
    }
    
    int result = (maxFreq - 1) * (n + 1) + maxCount;
    return (result > tasksSize) ? result : tasksSize;
}

45)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Create a new node
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Insert into BST (for creating a sample tree)
struct Node* insertBST(struct Node* root, int data) {
    if(root == NULL) {
        return createNode(data);
    }
    
    if(data < root->data) {
        root->left = insertBST(root->left, data);
    } else if(data > root->data) {
        root->right = insertBST(root->right, data);
    }
    
    return root;
}

// Calculate height of binary tree (recursive)
int height(struct Node* root) {
    if(root == NULL) {
        return 0;
    }
    
    int leftHeight = height(root->left);
    int rightHeight = height(root->right);
    
    return (leftHeight > rightHeight) ? leftHeight + 1 : rightHeight + 1;
}

// Calculate height using iterative approach (level order)
int heightIterative(struct Node* root) {
    if(root == NULL) return 0;
    
    struct Node* queue[100];
    int front = 0, rear = 0;
    int height = 0;
    
    queue[rear++] = root;
    queue[rear++] = NULL;  // Level marker
    
    while(front < rear) {
        struct Node* current = queue[front++];
        
        if(current == NULL) {
            height++;
            if(front < rear) {
                queue[rear++] = NULL;
            }
        } else {
            if(current->left != NULL) {
                queue[rear++] = current->left;
            }
            if(current->right != NULL) {
                queue[rear++] = current->right;
            }
        }
    }
    
    return height;
}

// Inorder traversal
void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int n, val;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insertBST(root, val);
    }
    
    printf("\nInorder traversal: ");
    inorder(root);
    printf("\n");
    
    int treeHeight = height(root);
    printf("Height of tree (recursive): %d\n", treeHeight);
    
    int treeHeightIter = heightIterative(root);
    printf("Height of tree (iterative): %d\n", treeHeightIter);
    
    return 0;
}

b) /**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */

// Recursive solution
int maxDepth(struct TreeNode* root) {
    if(root == NULL) {
        return 0;
    }
    
    int leftDepth = maxDepth(root->left);
    int rightDepth = maxDepth(root->right);
    
    return (leftDepth > rightDepth ? leftDepth : rightDepth) + 1;
}

// Iterative solution using stack (DFS)
int maxDepthIterative(struct TreeNode* root) {
    if(root == NULL) return 0;
    
    struct TreeNode* stack[10000];
    int depthStack[10000];
    int top = -1;
    
    stack[++top] = root;
    depthStack[top] = 1;
    int maxDepth = 0;
    
    while(top >= 0) {
        struct TreeNode* node = stack[top];
        int depth = depthStack[top--];
        
        if(depth > maxDepth) maxDepth = depth;
        
        if(node->right != NULL) {
            stack[++top] = node->right;
            depthStack[top] = depth + 1;
        }
        if(node->left != NULL) {
            stack[++top] = node->left;
            depthStack[top] = depth + 1;
        }
    }
    
    return maxDepth;
}

