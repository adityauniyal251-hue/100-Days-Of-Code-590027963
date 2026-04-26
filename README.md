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

46)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Insert into BST
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

// Inorder Traversal (Left - Root - Right)
void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

// Preorder Traversal (Root - Left - Right)
void preorder(struct Node* root) {
    if(root != NULL) {
        printf("%d ", root->data);
        preorder(root->left);
        preorder(root->right);
    }
}

// Postorder Traversal (Left - Right - Root)
void postorder(struct Node* root) {
    if(root != NULL) {
        postorder(root->left);
        postorder(root->right);
        printf("%d ", root->data);
    }
}

// Level Order Traversal (BFS)
void levelOrder(struct Node* root) {
    if(root == NULL) return;
    
    struct Node* queue[100];
    int front = 0, rear = 0;
    
    queue[rear++] = root;
    
    while(front < rear) {
        struct Node* current = queue[front++];
        printf("%d ", current->data);
        
        if(current->left != NULL) {
            queue[rear++] = current->left;
        }
        if(current->right != NULL) {
            queue[rear++] = current->right;
        }
    }
}

int main() {
    struct Node* root = NULL;
    int n, val, choice;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insertBST(root, val);
    }
    
    printf("\nChoose traversal:\n");
    printf("1. Inorder\n");
    printf("2. Preorder\n");
    printf("3. Postorder\n");
    printf("4. Level Order\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    printf("\nTraversal result: ");
    switch(choice) {
        case 1:
            inorder(root);
            break;
        case 2:
            preorder(root);
            break;
        case 3:
            postorder(root);
            break;
        case 4:
            levelOrder(root);
            break;
        default:
            printf("Invalid choice");
    }
    printf("\n");
    
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
void inorderHelper(struct TreeNode* root, int* result, int* size) {
    if(root == NULL) return;
    
    inorderHelper(root->left, result, size);
    result[(*size)++] = root->val;
    inorderHelper(root->right, result, size);
}

int* inorderTraversal(struct TreeNode* root, int* returnSize) {
    int* result = (int*)malloc(100 * sizeof(int));
    *returnSize = 0;
    inorderHelper(root, result, returnSize);
    return result;
}

// Iterative solution using stack
int* inorderTraversalIterative(struct TreeNode* root, int* returnSize) {
    int* result = (int*)malloc(100 * sizeof(int));
    *returnSize = 0;
    
    struct TreeNode* stack[100];
    int top = -1;
    struct TreeNode* current = root;
    
    while(current != NULL || top != -1) {
        while(current != NULL) {
            stack[++top] = current;
            current = current->left;
        }
        
        current = stack[top--];
        result[(*returnSize)++] = current->val;
        current = current->right;
    }
    
    return result;
}

47)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insertBST(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insertBST(root->left, data);
    else if(data > root->data) root->right = insertBST(root->right, data);
    return root;
}

// Level order traversal with level markers
void levelOrderWithLevels(struct Node* root) {
    if(root == NULL) return;
    
    struct Node* queue[100];
    int front = 0, rear = 0;
    int level = 0;
    
    queue[rear++] = root;
    queue[rear++] = NULL;  // Level marker
    
    printf("Level %d: ", level);
    
    while(front < rear) {
        struct Node* current = queue[front++];
        
        if(current == NULL) {
            if(front < rear) {
                level++;
                printf("\nLevel %d: ", level);
                queue[rear++] = NULL;
            }
        } else {
            printf("%d ", current->data);
            
            if(current->left != NULL) {
                queue[rear++] = current->left;
            }
            if(current->right != NULL) {
                queue[rear++] = current->right;
            }
        }
    }
    printf("\n");
}

// Zigzag level order traversal (spiral)
void zigzagLevelOrder(struct Node* root) {
    if(root == NULL) return;
    
    struct Node* stack1[100];
    struct Node* stack2[100];
    int top1 = -1, top2 = -1;
    int leftToRight = 1;
    
    stack1[++top1] = root;
    
    printf("Zigzag Level Order:\n");
    
    while(top1 != -1) {
        while(top1 != -1) {
            struct Node* current = stack1[top1--];
            printf("%d ", current->data);
            
            if(leftToRight) {
                if(current->left) stack2[++top2] = current->left;
                if(current->right) stack2[++top2] = current->right;
            } else {
                if(current->right) stack2[++top2] = current->right;
                if(current->left) stack2[++top2] = current->left;
            }
        }
        
        printf("\n");
        leftToRight = !leftToRight;
        
        // Swap stacks
        struct Node** tempStack = stack1;
        int tempTop = top1;
        stack1 = stack2;
        top1 = top2;
        stack2 = tempStack;
        top2 = tempTop;
    }
}

int main() {
    struct Node* root = NULL;
    int n, val, choice;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insertBST(root, val);
    }
    
    printf("\nChoose operation:\n");
    printf("1. Level Order with Levels\n");
    printf("2. Zigzag Level Order\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    if(choice == 1) {
        levelOrderWithLevels(root);
    } else {
        zigzagLevelOrder(root);
    }
    
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

int** levelOrder(struct TreeNode* root, int* returnSize, int** returnColumnSizes) {
    if(root == NULL) {
        *returnSize = 0;
        return NULL;
    }
    
    int** result = (int**)malloc(2000 * sizeof(int*));
    *returnColumnSizes = (int*)malloc(2000 * sizeof(int));
    *returnSize = 0;
    
    struct TreeNode* queue[2000];
    int front = 0, rear = 0;
    
    queue[rear++] = root;
    
    while(front < rear) {
        int levelSize = rear - front;
        (*returnColumnSizes)[*returnSize] = levelSize;
        result[*returnSize] = (int*)malloc(levelSize * sizeof(int));
        
        for(int i = 0; i < levelSize; i++) {
            struct TreeNode* node = queue[front++];
            result[*returnSize][i] = node->val;
            
            if(node->left) queue[rear++] = node->left;
            if(node->right) queue[rear++] = node->right;
        }
        (*returnSize)++;
    }
    
    return result;
}

48)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insertBST(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insertBST(root->left, data);
    else if(data > root->data) root->right = insertBST(root->right, data);
    return root;
}

// Count leaf nodes recursively
int countLeaves(struct Node* root) {
    if(root == NULL) return 0;
    
    if(root->left == NULL && root->right == NULL) {
        return 1;
    }
    
    return countLeaves(root->left) + countLeaves(root->right);
}

// Count non-leaf nodes
int countNonLeaves(struct Node* root) {
    if(root == NULL) return 0;
    
    if(root->left == NULL && root->right == NULL) {
        return 0;
    }
    
    return 1 + countNonLeaves(root->left) + countNonLeaves(root->right);
}

// Count total nodes
int countNodes(struct Node* root) {
    if(root == NULL) return 0;
    return 1 + countNodes(root->left) + countNodes(root->right);
}

// Print all leaf nodes
void printLeaves(struct Node* root) {
    if(root == NULL) return;
    
    if(root->left == NULL && root->right == NULL) {
        printf("%d ", root->data);
        return;
    }
    
    printLeaves(root->left);
    printLeaves(root->right);
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
    
    printf("\nTotal nodes: %d\n", countNodes(root));
    printf("Leaf nodes: %d\n", countLeaves(root));
    printf("Non-leaf nodes: %d\n", countNonLeaves(root));
    printf("Leaf values: ");
    printLeaves(root);
    printf("\n");
    
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

int sumOfLeftLeaves(struct TreeNode* root) {
    if(root == NULL) return 0;
    
    int sum = 0;
    
    // Check if left child exists and is a leaf
    if(root->left != NULL && root->left->left == NULL && root->left->right == NULL) {
        sum += root->left->val;
    }
    
    // Recursively check left and right subtrees
    sum += sumOfLeftLeaves(root->left);
    sum += sumOfLeftLeaves(root->right);
    
    return sum;
}

49)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Recursive insert
struct Node* insertRecursive(struct Node* root, int data) {
    if(root == NULL) {
        return createNode(data);
    }
    
    if(data < root->data) {
        root->left = insertRecursive(root->left, data);
    } else if(data > root->data) {
        root->right = insertRecursive(root->right, data);
    }
    // If equal, do nothing (no duplicates)
    
    return root;
}

// Iterative insert
struct Node* insertIterative(struct Node* root, int data) {
    struct Node* newNode = createNode(data);
    
    if(root == NULL) {
        return newNode;
    }
    
    struct Node* current = root;
    struct Node* parent = NULL;
    
    while(current != NULL) {
        parent = current;
        if(data < current->data) {
            current = current->left;
        } else if(data > current->data) {
            current = current->right;
        } else {
            // Duplicate not allowed
            free(newNode);
            return root;
        }
    }
    
    if(data < parent->data) {
        parent->left = newNode;
    } else {
        parent->right = newNode;
    }
    
    return root;
}

void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int n, val, choice, newVal;
    
    printf("Enter number of initial nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insertRecursive(root, val);
    }
    
    printf("\nBST (inorder): ");
    inorder(root);
    printf("\n");
    
    printf("\nChoose insert method:\n");
    printf("1. Recursive Insert\n");
    printf("2. Iterative Insert\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    printf("Enter value to insert: ");
    scanf("%d", &newVal);
    
    if(choice == 1) {
        root = insertRecursive(root, newVal);
    } else {
        root = insertIterative(root, newVal);
    }
    
    printf("BST after insertion (inorder): ");
    inorder(root);
    printf("\n");
    
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

struct TreeNode* insertIntoBST(struct TreeNode* root, int val) {
    if(root == NULL) {
        struct TreeNode* newNode = (struct TreeNode*)malloc(sizeof(struct TreeNode));
        newNode->val = val;
        newNode->left = NULL;
        newNode->right = NULL;
        return newNode;
    }
    
    if(val < root->val) {
        root->left = insertIntoBST(root->left, val);
    } else if(val > root->val) {
        root->right = insertIntoBST(root->right, val);
    }
    
    return root;
}

50)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insert(root->left, data);
    else if(data > root->data) root->right = insert(root->right, data);
    return root;
}

// Recursive search
struct Node* searchRecursive(struct Node* root, int key) {
    if(root == NULL || root->data == key) {
        return root;
    }
    
    if(key < root->data) {
        return searchRecursive(root->left, key);
    }
    return searchRecursive(root->right, key);
}

// Iterative search
struct Node* searchIterative(struct Node* root, int key) {
    struct Node* current = root;
    
    while(current != NULL) {
        if(current->data == key) {
            return current;
        } else if(key < current->data) {
            current = current->left;
        } else {
            current = current->right;
        }
    }
    
    return NULL;
}

// Find minimum value node
struct Node* findMin(struct Node* root) {
    if(root == NULL) return NULL;
    
    struct Node* current = root;
    while(current->left != NULL) {
        current = current->left;
    }
    return current;
}

// Find maximum value node
struct Node* findMax(struct Node* root) {
    if(root == NULL) return NULL;
    
    struct Node* current = root;
    while(current->right != NULL) {
        current = current->right;
    }
    return current;
}

void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int n, val, key, choice;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insert(root, val);
    }
    
    printf("\nBST (inorder): ");
    inorder(root);
    printf("\n");
    
    printf("\nMinimum value: %d\n", findMin(root)->data);
    printf("Maximum value: %d\n", findMax(root)->data);
    
    printf("\nChoose search method:\n");
    printf("1. Recursive Search\n");
    printf("2. Iterative Search\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    printf("Enter value to search: ");
    scanf("%d", &key);
    
    struct Node* result;
    if(choice == 1) {
        result = searchRecursive(root, key);
    } else {
        result = searchIterative(root, key);
    }
    
    if(result != NULL) {
        printf("Found: %d\n", result->data);
    } else {
        printf("Not found\n");
    }
    
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

struct TreeNode* searchBST(struct TreeNode* root, int val) {
    if(root == NULL || root->val == val) {
        return root;
    }
    
    if(val < root->val) {
        return searchBST(root->left, val);
    }
    return searchBST(root->right, val);
}

51)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insert(root->left, data);
    else if(data > root->data) root->right = insert(root->right, data);
    return root;
}

// Recursive LCA
struct Node* lowestCommonAncestorRecursive(struct Node* root, struct Node* p, struct Node* q) {
    if(root == NULL) return NULL;
    
    // If both values are smaller, LCA is in left subtree
    if(p->data < root->data && q->data < root->data) {
        return lowestCommonAncestorRecursive(root->left, p, q);
    }
    // If both values are larger, LCA is in right subtree
    else if(p->data > root->data && q->data > root->data) {
        return lowestCommonAncestorRecursive(root->right, p, q);
    }
    // Otherwise, current node is the LCA
    else {
        return root;
    }
}

// Iterative LCA
struct Node* lowestCommonAncestorIterative(struct Node* root, struct Node* p, struct Node* q) {
    struct Node* current = root;
    
    while(current != NULL) {
        if(p->data < current->data && q->data < current->data) {
            current = current->left;
        } else if(p->data > current->data && q->data > current->data) {
            current = current->right;
        } else {
            return current;
        }
    }
    
    return NULL;
}

// Find node by value
struct Node* findNode(struct Node* root, int val) {
    if(root == NULL || root->data == val) return root;
    
    if(val < root->data) return findNode(root->left, val);
    return findNode(root->right, val);
}

void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int n, val, val1, val2, choice;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insert(root, val);
    }
    
    printf("\nBST (inorder): ");
    inorder(root);
    printf("\n");
    
    printf("\nEnter two node values to find LCA: ");
    scanf("%d %d", &val1, &val2);
    
    struct Node* p = findNode(root, val1);
    struct Node* q = findNode(root, val2);
    
    if(p == NULL || q == NULL) {
        printf("One or both nodes not found!\n");
        return 1;
    }
    
    printf("\nChoose method:\n");
    printf("1. Recursive LCA\n");
    printf("2. Iterative LCA\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    struct Node* lca;
    if(choice == 1) {
        lca = lowestCommonAncestorRecursive(root, p, q);
    } else {
        lca = lowestCommonAncestorIterative(root, p, q);
    }
    
    if(lca != NULL) {
        printf("Lowest Common Ancestor of %d and %d is: %d\n", val1, val2, lca->data);
    } else {
        printf("LCA not found\n");
    }
    
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

struct TreeNode* lowestCommonAncestor(struct TreeNode* root, struct TreeNode* p, struct TreeNode* q) {
    struct TreeNode* current = root;
    
    while(current != NULL) {
        if(p->val < current->val && q->val < current->val) {
            current = current->left;
        } else if(p->val > current->val && q->val > current->val) {
            current = current->right;
        } else {
            return current;
        }
    }
    
    return NULL;
}

// Recursive version
struct TreeNode* lowestCommonAncestorRecursive(struct TreeNode* root, struct TreeNode* p, struct TreeNode* q) {
    if(root == NULL) return NULL;
    
    if(p->val < root->val && q->val < root->val) {
        return lowestCommonAncestorRecursive(root->left, p, q);
    } else if(p->val > root->val && q->val > root->val) {
        return lowestCommonAncestorRecursive(root->right, p, q);
    } else {
        return root;
    }
}

52)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insert(root->left, data);
    else if(data > root->data) root->right = insert(root->right, data);
    return root;
}

// Print array
void printPath(int path[], int pathLen) {
    for(int i = 0; i < pathLen; i++) {
        printf("%d", path[i]);
        if(i < pathLen - 1) printf(" -> ");
    }
    printf("\n");
}

// Print all root-to-leaf paths recursively
void printPathsRecursive(struct Node* root, int path[], int pathLen) {
    if(root == NULL) return;
    
    path[pathLen] = root->data;
    pathLen++;
    
    if(root->left == NULL && root->right == NULL) {
        printPath(path, pathLen);
    } else {
        printPathsRecursive(root->left, path, pathLen);
        printPathsRecursive(root->right, path, pathLen);
    }
}

// Find paths with a given sum
void findPathsWithSum(struct Node* root, int targetSum, int path[], int pathLen, int currentSum) {
    if(root == NULL) return;
    
    currentSum += root->data;
    path[pathLen] = root->data;
    pathLen++;
    
    if(root->left == NULL && root->right == NULL && currentSum == targetSum) {
        printPath(path, pathLen);
    }
    
    findPathsWithSum(root->left, targetSum, path, pathLen, currentSum);
    findPathsWithSum(root->right, targetSum, path, pathLen, currentSum);
}

void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int n, val, sum;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insert(root, val);
    }
    
    printf("\nBST (inorder): ");
    inorder(root);
    printf("\n");
    
    int path[100];
    printf("\nRoot-to-leaf paths:\n");
    printPathsRecursive(root, path, 0);
    
    printf("\nEnter target sum: ");
    scanf("%d", &sum);
    printf("Paths with sum %d:\n", sum);
    findPathsWithSum(root, sum, path, 0, 0);
    
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

void dfs(struct TreeNode* root, char** result, int* returnSize, char* path, int pathLen) {
    if(root == NULL) return;
    
    if(root->left == NULL && root->right == NULL) {
        // Leaf node - add current value to path and save
        char* newPath = (char*)malloc((pathLen + 12) * sizeof(char));
        sprintf(newPath, "%s%d", path, root->val);
        result[*returnSize] = newPath;
        (*returnSize)++;
        return;
    }
    
    char* newPath = (char*)malloc((pathLen + 12) * sizeof(char));
    sprintf(newPath, "%s%d->", path, root->val);
    
    dfs(root->left, result, returnSize, newPath, strlen(newPath));
    dfs(root->right, result, returnSize, newPath, strlen(newPath));
    
    free(newPath);
}

char** binaryTreePaths(struct TreeNode* root, int* returnSize) {
    char** result = (char**)malloc(100 * sizeof(char*));
    *returnSize = 0;
    
    if(root == NULL) return result ;
   
   dfs(root, result, returSIZE,"",0);

   return result ;

}

53)

a) #include <stdio.h>
#include <stdlib.h>
#include <limits.h>
#include <stdbool.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insert(root->left, data);
    else if(data > root->data) root->right = insert(root->right, data);
    return root;
}

// Method 1: Using inorder traversal (returns if inorder is sorted)
void inorderArray(struct Node* root, int arr[], int* index) {
    if(root != NULL) {
        inorderArray(root->left, arr, index);
        arr[(*index)++] = root->data;
        inorderArray(root->right, arr, index);
    }
}

bool isBSTInorder(struct Node* root) {
    int arr[100];
    int index = 0;
    inorderArray(root, arr, &index);
    
    for(int i = 1; i < index; i++) {
        if(arr[i] <= arr[i-1]) {
            return false;
        }
    }
    return true;
}

// Method 2: Using range checking (efficient)
bool isBSTUtil(struct Node* root, int min, int max) {
    if(root == NULL) return true;
    
    if(root->data <= min || root->data >= max) {
        return false;
    }
    
    return isBSTUtil(root->left, min, root->data) &&
           isBSTUtil(root->right, root->data, max);
}

bool isBST(struct Node* root) {
    return isBSTUtil(root, INT_MIN, INT_MAX);
}

// Method 3: Using previous node tracking (inorder with prev)
bool isBSTInorderPrev(struct Node* root, struct Node** prev) {
    if(root == NULL) return true;
    
    if(!isBSTInorderPrev(root->left, prev)) {
        return false;
    }
    
    if(*prev != NULL && root->data <= (*prev)->data) {
        return false;
    }
    *prev = root;
    
    return isBSTInorderPrev(root->right, prev);
}

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
        root = insert(root, val);
    }
    
    printf("\nBST (inorder): ");
    inorder(root);
    printf("\n");
    
    if(isBST(root)) {
        printf("This is a valid BST\n");
    } else {
        printf("This is NOT a valid BST\n");
    }
    
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

bool isValidBSTUtil(struct TreeNode* root, long long min, long long max) {
    if(root == NULL) return true;
    
    if(root->val <= min || root->val >= max) {
        return false;
    }
    
    return isValidBSTUtil(root->left, min, root->val) &&
           isValidBSTUtil(root->right, root->val, max);
}

bool isValidBST(struct TreeNode* root) {
    return isValidBSTUtil(root, LONG_LONG_MIN, LONG_LONG_MAX);
}

54)

a) #include <stdio.h>
#include <stdlib.h>
#include <limits.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insert(root->left, data);
    else if(data > root->data) root->right = insert(root->right, data);
    return root;
}

int max(int a, int b, int c) {
    int maxVal = (a > b) ? a : b;
    return (maxVal > c) ? maxVal : c;
}

int maxPathSumUtil(struct Node* root, int* globalMax) {
    if(root == NULL) return 0;
    
    int leftSum = maxPathSumUtil(root->left, globalMax);
    int rightSum = maxPathSumUtil(root->right, globalMax);
    
    // Maximum sum starting from root going through left or right
    int maxSingle = root->data;
    if(leftSum > 0) maxSingle += leftSum;
    if(rightSum > 0) maxSingle += rightSum;
    
    // Update global maximum (path that goes through root)
    pathSum = root->data;
    if(leftSum > 0) pathSum += leftSum;
    if(rightSum > 0) pathSum += rightSum;
    
    if(pathSum > *globalMax) {
        *globalMax = pathSum;
    }
    
    // Return max path sum starting from this node
    int result = root->data;
    int maxChild = (leftSum > rightSum) ? leftSum : rightSum;
    if(maxChild > 0) result += maxChild;
    
    return result;
}

int maxPathSum(struct Node* root) {
    int globalMax = INT_MIN;
    maxPathSumUtil(root, &globalMax);
    return globalMax;
}

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
        root = insert(root, val);
    }
    
    printf("\nBST (inorder): ");
    inorder(root);
    printf("\n");
    
    printf("Maximum path sum: %d\n", maxPathSum(root));
    
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

int max(int a, int b) {
    return (a > b) ? a : b;
}

int maxPathSumUtil(struct TreeNode* root, int* globalMax) {
    if(root == NULL) return 0;
    
    int leftSum = maxPathSumUtil(root->left, globalMax);
    int rightSum = maxPathSumUtil(root->right, globalMax);
    
    // Path through current node
    int pathThrough = root->val;
    if(leftSum > 0) pathThrough += leftSum;
    if(rightSum > 0) pathThrough += rightSum;
    
    if(pathThrough > *globalMax) {
        *globalMax = pathThrough;
    }
    
    // Return max path starting from current node
    int result = root->val;
    int maxChild = max(leftSum, rightSum);
    if(maxChild > 0) result += maxChild;
    
    return result;
}

int maxPathSum(struct TreeNode* root) {
    int globalMax = -1000000000;
    maxPathSumUtil(root, &globalMax);
    return globalMax;
}

55)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insert(root->left, data);
    else if(data > root->data) root->right = insert(root->right, data);
    return root;
}

int max(int a, int b) {
    return (a > b) ? a : b;
}

int height(struct Node* root) {
    if(root == NULL) return 0;
    return 1 + max(height(root->left), height(root->right));
}

int diameter(struct Node* root) {
    if(root == NULL) return 0;
    
    int leftHeight = height(root->left);
    int rightHeight = height(root->right);
    
    int leftDiameter = diameter(root->left);
    int rightDiameter = diameter(root->right);
    
    return max(leftHeight + rightHeight + 1, max(leftDiameter, rightDiameter));
}

// Optimized: return both height and diameter
int diameterOptimized(struct Node* root, int* height) {
    if(root == NULL) {
        *height = 0;
        return 0;
    }
    
    int leftHeight = 0, rightHeight = 0;
    int leftDiameter = diameterOptimized(root->left, &leftHeight);
    int rightDiameter = diameterOptimized(root->right, &rightHeight);
    
    *height = 1 + max(leftHeight, rightHeight);
    
    return max(leftHeight + rightHeight + 1, max(leftDiameter, rightDiameter));
}

void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int n, val, heightVal = 0;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insert(root, val);
    }
    
    printf("\nBST (inorder): ");
    inorder(root);
    printf("\n");
    
    printf("Diameter (simple): %d\n", diameter(root));
    printf("Diameter (optimized): %d\n", diameterOptimized(root, &heightVal));
    
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

int max(int a, int b) {
    return (a > b) ? a : b;
}

int diameterUtil(struct TreeNode* root, int* maxDiameter) {
    if(root == NULL) return 0;
    
    int leftHeight = diameterUtil(root->left, maxDiameter);
    int rightHeight = diameterUtil(root->right, maxDiameter);
    
    int currentDiameter = leftHeight + rightHeight;
    if(currentDiameter > *maxDiameter) {
        *maxDiameter = currentDiameter;
    }
    
    return 1 + max(leftHeight, rightHeight);
}

int diameterOfBinaryTree(struct TreeNode* root) {
    int maxDiameter = 0;
    diameterUtil(root, &maxDiameter);
    return maxDiameter;
}

56)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Build a symmetric tree manually (for demo)
struct Node* buildSymmetricTree() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(2);
    root->left->left = createNode(3);
    root->left->right = createNode(4);
    root->right->left = createNode(4);
    root->right->right = createNode(3);
    return root;
}

// Build an asymmetric tree
struct Node* buildAsymmetricTree() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(2);
    root->left->right = createNode(3);
    root->right->right = createNode(3);
    return root;
}

// Check if two trees are mirrors
bool isMirror(struct Node* left, struct Node* right) {
    if(left == NULL && right == NULL) return true;
    if(left == NULL || right == NULL) return false;
    
    return (left->data == right->data) &&
           isMirror(left->left, right->right) &&
           isMirror(left->right, right->left);
}

bool isSymmetric(struct Node* root) {
    if(root == NULL) return true;
    return isMirror(root->left, root->right);
}

// Iterative approach using queue
bool isSymmetricIterative(struct Node* root) {
    if(root == NULL) return true;
    
    struct Node* queue[200];
    int front = 0, rear = 0;
    
    queue[rear++] = root->left;
    queue[rear++] = root->right;
    
    while(front < rear) {
        struct Node* leftNode = queue[front++];
        struct Node* rightNode = queue[front++];
        
        if(leftNode == NULL && rightNode == NULL) continue;
        if(leftNode == NULL || rightNode == NULL) return false;
        if(leftNode->data != rightNode->data) return false;
        
        queue[rear++] = leftNode->left;
        queue[rear++] = rightNode->right;
        queue[rear++] = leftNode->right;
        queue[rear++] = rightNode->left;
    }
    
    return true;
}

void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    int choice;
    
    printf("Choose tree:\n");
    printf("1. Symmetric Tree\n");
    printf("2. Asymmetric Tree\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    struct Node* root;
    if(choice == 1) {
        root = buildSymmetricTree();
        printf("Symmetric Tree (inorder): ");
    } else {
        root = buildAsymmetricTree();
        printf("Asymmetric Tree (inorder): ");
    }
    inorder(root);
    printf("\n");
    
    if(isSymmetric(root)) {
        printf("The tree is symmetric (recursive)\n");
    } else {
        printf("The tree is NOT symmetric (recursive)\n");
    }
    
    if(isSymmetricIterative(root)) {
        printf("The tree is symmetric (iterative)\n");
    } else {
        printf("The tree is NOT symmetric (iterative)\n");
    }
    
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

bool isMirror(struct TreeNode* left, struct TreeNode* right) {
    if(left == NULL && right == NULL) return true;
    if(left == NULL || right == NULL) return false;
    
    return (left->val == right->val) &&
           isMirror(left->left, right->right) &&
           isMirror(left->right, right->left);
}

bool isSymmetric(struct TreeNode* root) {
    if(root == NULL) return true;
    return isMirror(root->left, root->right);
}

57)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insert(root->left, data);
    else if(data > root->data) root->right = insert(root->right, data);
    return root;
}

// Mirror the binary tree (swap left and right children)
void mirrorTree(struct Node* root) {
    if(root == NULL) return;
    
    // Swap left and right children
    struct Node* temp = root->left;
    root->left = root->right;
    root->right = temp;
    
    // Recursively mirror subtrees
    mirrorTree(root->left);
    mirrorTree(root->right);
}

// Check if two trees are mirrors
bool areMirrors(struct Node* a, struct Node* b) {
    if(a == NULL && b == NULL) return true;
    if(a == NULL || b == NULL) return false;
    
    return (a->data == b->data) &&
           areMirrors(a->left, b->right) &&
           areMirrors(a->right, b->left);
}

// Flatten tree to linked list (preorder order)
void flattenTree(struct Node* root) {
    if(root == NULL) return;
    
    flattenTree(root->left);
    flattenTree(root->right);
    
    struct Node* temp = root->right;
    root->right = root->left;
    root->left = NULL;
    
    struct Node* current = root;
    while(current->right != NULL) {
        current = current->right;
    }
    current->right = temp;
}

// Print tree as linked list (right pointers only)
void printFlattened(struct Node* root) {
    struct Node* current = root;
    while(current != NULL) {
        printf("%d -> ", current->data);
        current = current->right;
    }
    printf("NULL\n");
}

void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

void preorder(struct Node* root) {
    if(root != NULL) {
        printf("%d ", root->data);
        preorder(root->left);
        preorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int n, val, choice;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insert(root, val);
    }
    
    printf("\nOriginal BST (inorder): ");
    inorder(root);
    printf("\n");
    printf("Original BST (preorder): ");
    preorder(root);
    printf("\n");
    
    printf("\nChoose operation:\n");
    printf("1. Mirror the Tree\n");
    printf("2. Flatten to Linked List\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    if(choice == 1) {
        mirrorTree(root);
        printf("\nAfter mirroring (inorder): ");
        inorder(root);
        printf("\n");
        printf("After mirroring (preorder): ");
        preorder(root);
        printf("\n");
    } else {
        flattenTree(root);
        printf("\nFlattened tree as linked list: ");
        printFlattened(root);
    }
    
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

void flatten(struct TreeNode* root) {
    if(root == NULL) return;
    
    flatten(root->left);
    flatten(root->right);
    
    struct TreeNode* temp = root->right;
    root->right = root->left;
    root->left = NULL;
    
    struct TreeNode* current = root;
    while(current->right != NULL) {
        current = current->right;
    }
    current->right = temp;
}


58)

a)
 #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Search for an element in inorder array
int search(int inorder[], int start, int end, int val) {
    for(int i = start; i <= end; i++) {
        if(inorder[i] == val) {
            return i;
        }
    }
    return -1;
}

// Build tree from inorder and preorder traversals
struct Node* buildTreePreIn(int preorder[], int inorder[], int preStart, int preEnd, int inStart, int inEnd) {
    if(preStart > preEnd || inStart > inEnd) {
        return NULL;
    }
    
    int rootVal = preorder[preStart];
    struct Node* root = createNode(rootVal);
    
    int inIndex = search(inorder, inStart, inEnd, rootVal);
    int leftCount = inIndex - inStart;
    
    root->left = buildTreePreIn(preorder, inorder,
                                 preStart + 1, preStart + leftCount,
                                 inStart, inIndex - 1);
    root->right = buildTreePreIn(preorder, inorder,
                                  preStart + leftCount + 1, preEnd,
                                  inIndex + 1, inEnd);
    
    return root;
}

void inorderPrint(struct Node* root) {
    if(root != NULL) {
        inorderPrint(root->left);
        printf("%d ", root->data);
        inorderPrint(root->right);
    }
}

void preorderPrint(struct Node* root) {
    if(root != NULL) {
        printf("%d ", root->data);
        preorderPrint(root->left);
        preorderPrint(root->right);
    }
}

void postorderPrint(struct Node* root) {
    if(root != NULL) {
        postorderPrint(root->left);
        postorderPrint(root->right);
        printf("%d ", root->data);
    }
}

int main() {
    int inorder[100], preorder[100], n;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter inorder traversal: ");
    for(int i = 0; i < n; i++) {
        scanf("%d", &inorder[i]);
    }
    
    printf("Enter preorder traversal: ");
    for(int i = 0; i < n; i++) {
        scanf("%d", &preorder[i]);
    }
    
    struct Node* root = buildTreePreIn(preorder, inorder, 0, n - 1, 0, n - 1);
    
    printf("\nConstructed Tree:\n");
    printf("Inorder: ");
    inorderPrint(root);
    printf("\n");
    printf("Preorder: ");
    preorderPrint(root);
    printf("\n");
    printf("Postorder: ");
    postorderPrint(root);
    printf("\n");
    
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

int search(int* inorder, int start, int end, int val) {
    for(int i = start; i <= end; i++) {
        if(inorder[i] == val) return i;
    }
    return -1;
}

struct TreeNode* buildTreeUtil(int* preorder, int* inorder, int preStart, int preEnd, int inStart, int inEnd) {
    if(preStart > preEnd || inStart > inEnd) return NULL;
    
    struct TreeNode* root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
    root->val = preorder[preStart];
    root->left = NULL;
    root->right = NULL;
    
    int inIndex = search(inorder, inStart, inEnd, root->val);
    int leftCount = inIndex - inStart;
    
    root->left = buildTreeUtil(preorder, inorder,
                               preStart + 1, preStart + leftCount,
                               inStart, inIndex - 1);
    root->right = buildTreeUtil(preorder, inorder,
                                preStart + leftCount + 1, preEnd,
                                inIndex + 1, inEnd);
    
    return root;
}

struct TreeNode* buildTree(int* preorder, int preorderSize, int* inorder, int inorderSize) {
    return buildTreeUtil(preorder, inorder, 0, preorderSize - 1, 0, inorderSize - 1);
}

59)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

int search(int inorder[], int start, int end, int val) {
    for(int i = start; i <= end; i++) {
        if(inorder[i] == val) return i;
    }
    return -1;
}

// Build tree from inorder and postorder traversals
struct Node* buildTreePostIn(int postorder[], int inorder[], int postStart, int postEnd, int inStart, int inEnd) {
    if(postStart > postEnd || inStart > inEnd) {
        return NULL;
    }
    
    int rootVal = postorder[postEnd];  // Last element in postorder is root
    struct Node* root = createNode(rootVal);
    
    int inIndex = search(inorder, inStart, inEnd, rootVal);
    int leftCount = inIndex - inStart;
    
    // Left subtree: postStart to postStart + leftCount - 1
    root->left = buildTreePostIn(postorder, inorder,
                                  postStart, postStart + leftCount - 1,
                                  inStart, inIndex - 1);
    // Right subtree: postStart + leftCount to postEnd - 1
    root->right = buildTreePostIn(postorder, inorder,
                                   postStart + leftCount, postEnd - 1,
                                   inIndex + 1, inEnd);
    
    return root;
}

void inorderPrint(struct Node* root) {
    if(root != NULL) {
        inorderPrint(root->left);
        printf("%d ", root->data);
        inorderPrint(root->right);
    }
}

void preorderPrint(struct Node* root) {
    if(root != NULL) {
        printf("%d ", root->data);
        preorderPrint(root->left);
        preorderPrint(root->right);
    }
}

void postorderPrint(struct Node* root) {
    if(root != NULL) {
        postorderPrint(root->left);
        postorderPrint(root->right);
        printf("%d ", root->data);
    }
}

int main() {
    int inorder[100], postorder[100], n;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter inorder traversal: ");
    for(int i = 0; i < n; i++) {
        scanf("%d", &inorder[i]);
    }
    
    printf("Enter postorder traversal: ");
    for(int i = 0; i < n; i++) {
        scanf("%d", &postorder[i]);
    }
    
    struct Node* root = buildTreePostIn(postorder, inorder, 0, n - 1, 0, n - 1);
    
    printf("\nConstructed Tree:\n");
    printf("Inorder: ");
    inorderPrint(root);
    printf("\n");
    printf("Preorder: ");
    preorderPrint(root);
    printf("\n");
    printf("Postorder: ");
    postorderPrint(root);
    printf("\n");
    
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

int search(int* inorder, int start, int end, int val) {
    for(int i = start; i <= end; i++) {
        if(inorder[i] == val) return i;
    }
    return -1;
}

struct TreeNode* buildTreeUtil(int* inorder, int* postorder, int inStart, int inEnd, int postStart, int postEnd) {
    if(inStart > inEnd || postStart > postEnd) return NULL;
    
    struct TreeNode* root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
    root->val = postorder[postEnd];
    root->left = NULL;
    root->right = NULL;
    
    int inIndex = search(inorder, inStart, inEnd, root->val);
    int leftCount = inIndex - inStart;
    
    root->left = buildTreeUtil(inorder, postorder,
                               inStart, inIndex - 1,
                               postStart, postStart + leftCount - 1);
    root->right = buildTreeUtil(inorder, postorder,
                                inIndex + 1, inEnd,
                                postStart + leftCount, postEnd - 1);
    
    return root;
}

struct TreeNode* buildTree(int* inorder, int inorderSize, int* postorder, int postorderSize) {
    return buildTreeUtil(inorder, postorder, 0, inorderSize - 1, 0, postorderSize - 1);
}

60)

a) #include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int data) {
    if(root == NULL) return createNode(data);
    if(data < root->data) root->left = insert(root->left, data);
    else if(data > root->data) root->right = insert(root->right, data);
    return root;
}

// Reverse level order (bottom-up)
void reverseLevelOrder(struct Node* root) {
    if(root == NULL) return;
    
    struct Node* queue[100];
    int result[100][100];
    int levelSizes[100];
    int front = 0, rear = 0;
    int level = 0;
    
    queue[rear++] = root;
    queue[rear++] = NULL;
    
    while(front < rear) {
        struct Node* current = queue[front++];
        
        if(current == NULL) {
            if(front < rear) {
                level++;
                queue[rear++] = NULL;
            }
        } else {
            result[level][levelSizes[level]++] = current->data;
            
            if(current->left != NULL) queue[rear++] = current->left;
            if(current->right != NULL) queue[rear++] = current->right;
        }
    }
    
    printf("Reverse Level Order (bottom-up):\n");
    for(int i = level; i >= 0; i--) {
        printf("Level %d: ", i);
        for(int j = 0; j < levelSizes[i]; j++) {
            printf("%d ", result[i][j]);
        }
        printf("\n");
    }
}

// Zigzag level order (spiral)
void zigzagLevelOrder(struct Node* root) {
    if(root == NULL) return;
    
    struct Node* stack1[100];
    struct Node* stack2[100];
    int top1 = -1, top2 = -1;
    int leftToRight = 1;
    
    stack1[++top1] = root;
    
    printf("Zigzag Level Order:\n");
    int level = 0;
    
    while(top1 != -1) {
        printf("Level %d: ", level);
        
        while(top1 != -1) {
            struct Node* current = stack1[top1--];
            printf("%d ", current->data);
            
            if(leftToRight) {
                if(current->left) stack2[++top2] = current->left;
                if(current->right) stack2[++top2] = current->right;
            } else {
                if(current->right) stack2[++top2] = current->right;
                if(current->left) stack2[++top2] = current->left;
            }
        }
        
        printf("\n");
        leftToRight = !leftToRight;
        level++;
        
        // Swap stacks
        struct Node** tempStack = stack1;
        int tempTop = top1;
        stack1 = stack2;
        top1 = top2;
        stack2 = tempStack;
        top2 = tempTop;
    }
}

void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int n, val, choice;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    printf("Enter %d values: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &val);
        root = insert(root, val);
    }
    
    printf("\nBST (inorder): ");
    inorder(root);
    printf("\n");
    
    printf("\nChoose operation:\n");
    printf("1. Reverse Level Order (Bottom-up)\n");
    printf("2. Zigzag Level Order (Spiral)\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    if(choice == 1) {
        reverseLevelOrder(root);
    } else {
        zigzagLevelOrder(root);
    }
    
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

int** levelOrderBottom(struct TreeNode* root, int* returnSize, int** returnColumnSizes) {
    if(root == NULL) {
        *returnSize = 0;
        return NULL;
    }
    
    int** result = (int**)malloc(2000 * sizeof(int*));
    *returnColumnSizes = (int*)malloc(2000 * sizeof(int));
    *returnSize = 0;
    
    struct TreeNode* queue[2000];
    int front = 0, rear = 0;
    
    queue[rear++] = root;
    
    while(front < rear) {
        int levelSize = rear - front;
        (*returnColumnSizes)[*returnSize] = levelSize;
        result[*returnSize] = (int*)malloc(levelSize * sizeof(int));
        
        for(int i = 0; i < levelSize; i++) {
            struct TreeNode* node = queue[front++];
            result[*returnSize][i] = node->val;
            
            if(node->left) queue[rear++] = node->left;
            if(node->right) queue[rear++] = node->right;
        }
        (*returnSize)++;
    }
    
    // Reverse the result array for bottom-up order
    for(int i = 0; i < *returnSize / 2; i++) {
        int* tempArr = result[i];
        result[i] = result[*returnSize - 1 - i];
        result[*returnSize - 1 - i] = tempArr;
        
        int tempCol = (*returnColumnSizes)[i];
        (*returnColumnSizes)[i] = (*returnColumnSizes)[*returnSize - 1 - i];
        (*returnColumnSizes)[*returnSize - 1 - i] = tempCol;
    }
    
    return result;
}

61)

a) #include <stdio.h>
#include <stdbool.h>

#define MAX 100

typedef struct {
    int vertices;
    int adjMatrix[MAX][MAX];
} Graph;

// Initialize graph
void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            g->adjMatrix[i][j] = 0;
        }
    }
}

// Add edge (undirected)
void addEdgeUndirected(Graph* g, int u, int v) {
    if(u >= 0 && u < g->vertices && v >= 0 && v < g->vertices) {
        g->adjMatrix[u][v] = 1;
        g->adjMatrix[v][u] = 1;
    }
}

// Add edge (directed)
void addEdgeDirected(Graph* g, int u, int v) {
    if(u >= 0 && u < g->vertices && v >= 0 && v < g->vertices) {
        g->adjMatrix[u][v] = 1;
    }
}

// Remove edge
void removeEdge(Graph* g, int u, int v) {
    if(u >= 0 && u < g->vertices && v >= 0 && v < g->vertices) {
        g->adjMatrix[u][v] = 0;
        g->adjMatrix[v][u] = 0;
    }
}

// Check if edge exists
bool hasEdge(Graph* g, int u, int v) {
    return g->adjMatrix[u][v] == 1;
}

// Get degree of vertex (for undirected graph)
int getDegree(Graph* g, int vertex) {
    int degree = 0;
    for(int i = 0; i < g->vertices; i++) {
        if(g->adjMatrix[vertex][i] == 1) {
            degree++;
        }
    }
    return degree;
}

// Print adjacency matrix
void printGraph(Graph* g) {
    printf("Adjacency Matrix:\n   ");
    for(int i = 0; i < g->vertices; i++) {
        printf("%2d ", i);
    }
    printf("\n");
    
    for(int i = 0; i < g->vertices; i++) {
        printf("%2d ", i);
        for(int j = 0; j < g->vertices; j++) {
            printf("%2d ", g->adjMatrix[i][j]);
        }
        printf("\n");
    }
}

int main() {
    Graph g;
    int vertices, edges, choice, u, v;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("\nChoose graph type:\n");
    printf("1. Undirected\n");
    printf("2. Directed\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    for(int i = 0; i < edges; i++) {
        printf("Edge %d (u v): ", i + 1);
        scanf("%d %d", &u, &v);
        
        if(choice == 1) {
            addEdgeUndirected(&g, u, v);
        } else {
            addEdgeDirected(&g, u, v);
        }
    }
    
    printGraph(&g);
    
    printf("\nDegree of vertices:\n");
    for(int i = 0; i < vertices; i++) {
        printf("Vertex %d: %d\n", i, getDegree(&g, i));
    }
    
    return 0;
}

b) void dfs(int** isConnected, int n, int city, int* visited) {
    visited[city] = 1;
    
    for(int i = 0; i < n; i++) {
        if(isConnected[city][i] == 1 && !visited[i]) {
            dfs(isConnected, n, i, visited);
        }
    }
}

int findCircleNum(int** isConnected, int isConnectedSize, int* isConnectedColSize) {
    int n = isConnectedSize;
    int* visited = (int*)calloc(n, sizeof(int));
    int provinces = 0;
    
    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            dfs(isConnected, n, i, visited);
            provinces++;
        }
    }
    
    free(visited);
    return provinces;
}

62)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 100

// Node in adjacency list
struct AdjListNode {
    int dest;
    int weight;  // For weighted graphs
    struct AdjListNode* next;
};

// Adjacency list for a vertex
struct AdjList {
    struct AdjListNode* head;
};

// Graph structure
typedef struct {
    int vertices;
    struct AdjList array[MAX];
    int isWeighted;
} Graph;

// Create a new adjacency list node
struct AdjListNode* createNode(int dest, int weight) {
    struct AdjListNode* newNode = (struct AdjListNode*)malloc(sizeof(struct AdjListNode));
    newNode->dest = dest;
    newNode->weight = weight;
    newNode->next = NULL;
    return newNode;
}

// Initialize graph
void initGraph(Graph* g, int vertices, int isWeighted) {
    g->vertices = vertices;
    g->isWeighted = isWeighted;
    for(int i = 0; i < vertices; i++) {
        g->array[i].head = NULL;
    }
}

// Add edge (undirected)
void addEdgeUndirected(Graph* g, int src, int dest, int weight) {
    // Add edge src -> dest
    struct AdjListNode* newNode = createNode(dest, weight);
    newNode->next = g->array[src].head;
    g->array[src].head = newNode;
    
    // Add edge dest -> src (for undirected)
    newNode = createNode(src, weight);
    newNode->next = g->array[dest].head;
    g->array[dest].head = newNode;
}

// Add edge (directed)
void addEdgeDirected(Graph* g, int src, int dest, int weight) {
    struct AdjListNode* newNode = createNode(dest, weight);
    newNode->next = g->array[src].head;
    g->array[src].head = newNode;
}

// Print adjacency list
void printGraph(Graph* g) {
    printf("Adjacency List:\n");
    for(int i = 0; i < g->vertices; i++) {
        printf("Vertex %d: ", i);
        struct AdjListNode* current = g->array[i].head;
        while(current != NULL) {
            if(g->isWeighted) {
                printf("-> (%d, w=%d) ", current->dest, current->weight);
            } else {
                printf("-> %d ", current->dest);
            }
            current = current->next;
        }
        printf("-> NULL\n");
    }
}

// Get degree of vertex
int getDegree(Graph* g, int vertex) {
    int degree = 0;
    struct AdjListNode* current = g->array[vertex].head;
    while(current != NULL) {
        degree++;
        current = current->next;
    }
    return degree;
}

// BFS traversal using adjacency list
void bfs(Graph* g, int start) {
    bool visited[MAX] = {false};
    int queue[MAX], front = 0, rear = 0;
    
    visited[start] = true;
    queue[rear++] = start;
    
    printf("BFS Traversal starting from %d: ", start);
    
    while(front < rear) {
        int current = queue[front++];
        printf("%d ", current);
        
        struct AdjListNode* neighbor = g->array[current].head;
        while(neighbor != NULL) {
            if(!visited[neighbor->dest]) {
                visited[neighbor->dest] = true;
                queue[rear++] = neighbor->dest;
            }
            neighbor = neighbor->next;
        }
    }
    printf("\n");
}

int main() {
    Graph g;
    int vertices, edges, choice, src, dest, weight;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    
    printf("Choose graph type:\n");
    printf("1. Unweighted\n");
    printf("2. Weighted\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    initGraph(&g, vertices, (choice == 2));
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    printf("Choose edge direction:\n");
    printf("1. Undirected\n");
    printf("2. Directed\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    for(int i = 0; i < edges; i++) {
        if(g.isWeighted) {
            printf("Edge %d (src dest weight): ", i + 1);
            scanf("%d %d %d", &src, &dest, &weight);
        } else {
            printf("Edge %d (src dest): ", i + 1);
            scanf("%d %d", &src, &dest);
            weight = 1;
        }
        
        if(choice == 1) {
            addEdgeUndirected(&g, src, dest, weight);
        } else {
            addEdgeDirected(&g, src, dest, weight);
        }
    }
    
    printGraph(&g);
    
    printf("\nDegrees:\n");
    for(int i = 0; i < vertices; i++) {
        printf("Vertex %d: %d\n", i, getDegree(&g, i));
    }
    
    bfs(&g, 0);
    
    return 0;
}

b) void dfs(int** rooms, int* roomsColSize, int room, int* visited, int n) {
    visited[room] = 1;
    
    for(int i = 0; i < roomsColSize[room]; i++) {
        int key = rooms[room][i];
        if(!visited[key]) {
            dfs(rooms, roomsColSize, key, visited, n);
        }
    }
}

bool canVisitAllRooms(int** rooms, int roomsSize, int* roomsColSize) {
    int* visited = (int*)calloc(roomsSize, sizeof(int));
    
    dfs(rooms, roomsColSize, 0, visited, roomsSize);
    
    for(int i = 0; i < roomsSize; i++) {
        if(!visited[i]) {
            free(visited);
            return false;
        }
    }
    
    free(visited);
    return true;
}

63)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 100

typedef struct {
    int vertices;
    int adjMatrix[MAX][MAX];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            g->adjMatrix[i][j] = 0;
        }
    }
}

void addEdge(Graph* g, int u, int v) {
    g->adjMatrix[u][v] = 1;
    g->adjMatrix[v][u] = 1;
}

// Recursive DFS
void dfsRecursive(Graph* g, int vertex, bool* visited) {
    visited[vertex] = true;
    printf("%d ", vertex);
    
    for(int i = 0; i < g->vertices; i++) {
        if(g->adjMatrix[vertex][i] == 1 && !visited[i]) {
            dfsRecursive(g, i, visited);
        }
    }
}

// Iterative DFS using stack
void dfsIterative(Graph* g, int start) {
    bool visited[MAX] = {false};
    int stack[MAX];
    int top = -1;
    
    stack[++top] = start;
    
    printf("DFS (Iterative): ");
    
    while(top >= 0) {
        int vertex = stack[top--];
        
        if(!visited[vertex]) {
            visited[vertex] = true;
            printf("%d ", vertex);
            
            // Push neighbors in reverse order for correct order
            for(int i = g->vertices - 1; i >= 0; i--) {
                if(g->adjMatrix[vertex][i] == 1 && !visited[i]) {
                    stack[++top] = i;
                }
            }
        }
    }
    printf("\n");
}

// Find connected components using DFS
void findConnectedComponents(Graph* g) {
    bool visited[MAX] = {false};
    int componentCount = 0;
    
    printf("Connected Components:\n");
    
    for(int i = 0; i < g->vertices; i++) {
        if(!visited[i]) {
            componentCount++;
            printf("Component %d: ", componentCount);
            dfsRecursive(g, i, visited);
            printf("\n");
        }
    }
    
    printf("Total components: %d\n", componentCount);
}

void printGraph(Graph* g) {
    printf("Adjacency Matrix:\n");
    for(int i = 0; i < g->vertices; i++) {
        for(int j = 0; j < g->vertices; j++) {
            printf("%d ", g->adjMatrix[i][j]);
        }
        printf("\n");
    }
}

int main() {
    Graph g;
    int vertices, edges, u, v, start;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    for(int i = 0; i < edges; i++) {
        printf("Edge %d (u v): ", i + 1);
        scanf("%d %d", &u, &v);
        addEdge(&g, u, v);
    }
    
    printGraph(&g);
    
    printf("\nEnter starting vertex for DFS: ");
    scanf("%d", &start);
    
    bool visited[MAX] = {false};
    printf("DFS (Recursive) from %d: ", start);
    dfsRecursive(&g, start, visited);
    printf("\n");
    
    dfsIterative(&g, start);
    
    findConnectedComponents(&g);
    
    return 0;
}

b) void dfs(int** image, int imageSize, int* imageColSize, int sr, int sc, int originalColor, int newColor) {
    if(sr < 0 || sr >= imageSize || sc < 0 || sc >= imageColSize[0]) {
        return;
    }
    if(image[sr][sc] != originalColor) {
        return;
    }
    if(image[sr][sc] == newColor) {
        return;
    }
    
    image[sr][sc] = newColor;
    
    dfs(image, imageSize, imageColSize, sr + 1, sc, originalColor, newColor);
    dfs(image, imageSize, imageColSize, sr - 1, sc, originalColor, newColor);
    dfs(image, imageSize, imageColSize, sr, sc + 1, originalColor, newColor);
    dfs(image, imageSize, imageColSize, sr, sc - 1, originalColor, newColor);
}

int** floodFill(int** image, int imageSize, int* imageColSize, int sr, int sc, int color, int* returnSize, int** returnColumnSizes) {
    *returnSize = imageSize;
    *returnColumnSizes = imageColSize;
    
    int originalColor = image[sr][sc];
    if(originalColor != color) {
        dfs(image, imageSize, imageColSize, sr, sc, originalColor, color);
    }
    
    return image;
}

64)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 100

typedef struct {
    int vertices;
    int adjMatrix[MAX][MAX];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            g->adjMatrix[i][j] = 0;
        }
    }
}

void addEdge(Graph* g, int u, int v) {
    g->adjMatrix[u][v] = 1;
    g->adjMatrix[v][u] = 1;
}

// BFS using queue
void bfs(Graph* g, int start) {
    bool visited[MAX] = {false};
    int queue[MAX];
    int front = 0, rear = 0;
    
    visited[start] = true;
    queue[rear++] = start;
    
    printf("BFS Traversal from %d: ", start);
    
    while(front < rear) {
        int vertex = queue[front++];
        printf("%d ", vertex);
        
        for(int i = 0; i < g->vertices; i++) {
            if(g->adjMatrix[vertex][i] == 1 && !visited[i]) {
                visited[i] = true;
                queue[rear++] = i;
            }
        }
    }
    printf("\n");
}

// BFS to find shortest path (unweighted graph)
void shortestPath(Graph* g, int start, int target) {
    bool visited[MAX] = {false};
    int queue[MAX];
    int front = 0, rear = 0;
    int parent[MAX];
    
    for(int i = 0; i < g->vertices; i++) {
        parent[i] = -1;
    }
    
    visited[start] = true;
    queue[rear++] = start;
    
    while(front < rear) {
        int vertex = queue[front++];
        
        if(vertex == target) {
            break;
        }
        
        for(int i = 0; i < g->vertices; i++) {
            if(g->adjMatrix[vertex][i] == 1 && !visited[i]) {
                visited[i] = true;
                parent[i] = vertex;
                queue[rear++] = i;
            }
        }
    }
    
    if(!visited[target]) {
        printf("No path from %d to %d\n", start, target);
        return;
    }
    
    // Print path
    int path[MAX], pathLen = 0;
    int current = target;
    while(current != -1) {
        path[pathLen++] = current;
        current = parent[current];
    }
    
    printf("Shortest path from %d to %d: ", start, target);
    for(int i = pathLen - 1; i >= 0; i--) {
        printf("%d ", path[i]);
    }
    printf("\n");
}

// Check if graph is connected using BFS
bool isConnected(Graph* g) {
    bool visited[MAX] = {false};
    int queue[MAX];
    int front = 0, rear = 0;
    int count = 0;
    
    visited[0] = true;
    queue[rear++] = 0;
    
    while(front < rear) {
        int vertex = queue[front++];
        count++;
        
        for(int i = 0; i < g->vertices; i++) {
            if(g->adjMatrix[vertex][i] == 1 && !visited[i]) {
                visited[i] = true;
                queue[rear++] = i;
            }
        }
    }
    
    return count == g->vertices;
}

void printGraph(Graph* g) {
    printf("Adjacency Matrix:\n");
    for(int i = 0; i < g->vertices; i++) {
        for(int j = 0; j < g->vertices; j++) {
            printf("%d ", g->adjMatrix[i][j]);
        }
        printf("\n");
    }
}

int main() {
    Graph g;
    int vertices, edges, u, v, start, target;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    for(int i = 0; i < edges; i++) {
        printf("Edge %d (u v): ", i + 1);
        scanf("%d %d", &u, &v);
        addEdge(&g, u, v);
    }
    
    printGraph(&g);
    
    printf("\nEnter starting vertex for BFS: ");
    scanf("%d", &start);
    bfs(&g, start);
    
    printf("\nEnter source and target for shortest path: ");
    scanf("%d %d", &start, &target);
    shortestPath(&g, start, target);
    
    if(isConnected(&g)) {
        printf("\nGraph is connected\n");
    } else {
        printf("\nGraph is NOT connected\n");
    }
    
    return 0;
}

b) #include <stdlib.h>
#include <limits.h>

int orangesRotting(int** grid, int gridSize, int* gridColSize) {
    int rows = gridSize;
    int cols = gridColSize[0];
    
    int queue[10000][2];
    int front = 0, rear = 0;
    int freshCount = 0;
    int minutes = 0;
    
    // Find all rotten oranges and count fresh ones
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < cols; j++) {
            if(grid[i][j] == 2) {
                queue[rear][0] = i;
                queue[rear][1] = j;
                rear++;
            } else if(grid[i][j] == 1) {
                freshCount++;
            }
        }
    }
    
    // If no fresh oranges, return 0
    if(freshCount == 0) return 0;
    
    // Directions: up, down, left, right
    int dirs[4][2] = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
    
    while(front < rear && freshCount > 0) {
        int levelSize = rear - front;
        minutes++;
        
        for(int i = 0; i < levelSize; i++) {
            int r = queue[front][0];
            int c = queue[front][1];
            front++;
            
            for(int d = 0; d < 4; d++) {
                int nr = r + dirs[d][0];
                int nc = c + dirs[d][1];
                
                if(nr >= 0 && nr < rows && nc >= 0 && nc < cols && grid[nr][nc] == 1) {
                    grid[nr][nc] = 2;
                    freshCount--;
                    queue[rear][0] = nr;
                    queue[rear][1] = nc;
                    rear++;
                }
            }
        }
    }
    
    return (freshCount == 0) ? minutes : -1;
}

65)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 100

typedef struct {
    int vertices;
    int adjMatrix[MAX][MAX];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            g->adjMatrix[i][j] = 0;
        }
    }
}

void addEdge(Graph* g, int u, int v) {
    g->adjMatrix[u][v] = 1;
    g->adjMatrix[v][u] = 1;
}

bool isCyclicUtil(Graph* g, int vertex, bool* visited, int parent) {
    visited[vertex] = true;
    
    for(int i = 0; i < g->vertices; i++) {
        if(g->adjMatrix[vertex][i] == 1) {
            if(!visited[i]) {
                if(isCyclicUtil(g, i, visited, vertex)) {
                    return true;
                }
            } else if(i != parent) {
                return true;
            }
        }
    }
    return false;
}

bool hasCycle(Graph* g) {
    bool visited[MAX] = {false};
    
    for(int i = 0; i < g->vertices; i++) {
        if(!visited[i]) {
            if(isCyclicUtil(g, i, visited, -1)) {
                return true;
            }
        }
    }
    return false;
}

// Detect cycle in directed graph using 3-state coloring
bool isCyclicDirectedUtil(Graph* g, int vertex, int* visited) {
    // 0 = unvisited, 1 = visiting (in recursion stack), 2 = fully processed
    if(visited[vertex] == 1) return true;
    if(visited[vertex] == 2) return false;
    
    visited[vertex] = 1;
    
    for(int i = 0; i < g->vertices; i++) {
        if(g->adjMatrix[vertex][i] == 1) {
            if(isCyclicDirectedUtil(g, i, visited)) {
                return true;
            }
        }
    }
    
    visited[vertex] = 2;
    return false;
}

bool hasCycleDirected(Graph* g) {
    int visited[MAX] = {0};
    
    for(int i = 0; i < g->vertices; i++) {
        if(visited[i] == 0) {
            if(isCyclicDirectedUtil(g, i, visited)) {
                return true;
            }
        }
    }
    return false;
}

int main() {
    Graph g;
    int vertices, edges, u, v, type;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Choose graph type:\n");
    printf("1. Undirected\n");
    printf("2. Directed\n");
    printf("Enter choice: ");
    scanf("%d", &type);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    for(int i = 0; i < edges; i++) {
        printf("Edge %d (u v): ", i + 1);
        scanf("%d %d", &u, &v);
        if(type == 1) {
            addEdge(&g, u, v);
        } else {
            g.adjMatrix[u][v] = 1;
        }
    }
    
    bool cycle;
    if(type == 1) {
        cycle = hasCycle(&g);
        printf("\nUndirected Graph ");
    } else {
        cycle = hasCycleDirected(&g);
        printf("\nDirected Graph ");
    }
    
    if(cycle) {
        printf("has a cycle\n");
    } else {
        printf("does NOT have a cycle\n");
    }
    
    return 0;
}

b) bool canFinish(int numCourses, int** prerequisites, int prerequisitesSize, int* prerequisitesColSize) {
    // Build adjacency list
    int** adj = (int**)malloc(numCourses * sizeof(int*));
    int* adjSize = (int*)calloc(numCourses, sizeof(int));
    
    for(int i = 0; i < numCourses; i++) {
        adj[i] = (int*)malloc(numCourses * sizeof(int));
    }
    
    for(int i = 0; i < prerequisitesSize; i++) {
        int course = prerequisites[i][0];
        int prereq = prerequisites[i][1];
        adj[prereq][adjSize[prereq]++] = course;
    }
    
    // 0 = unvisited, 1 = visiting, 2 = visited
    int* state = (int*)calloc(numCourses, sizeof(int));
    
    // DFS to detect cycle
    int* stack = (int*)malloc(numCourses * sizeof(int));
    
    for(int i = 0; i < numCourses; i++) {
        if(state[i] == 0) {
            int top = -1;
            stack[++top] = i;
            
            while(top >= 0) {
                int course = stack[top];
                
                if(state[course] == 0) {
                    state[course] = 1;
                    
                    for(int j = adjSize[course] - 1; j >= 0; j--) {
                        int next = adj[course][j];
                        if(state[next] == 1) {
                            // Cycle detected
                            free(adj);
                            free(adjSize);
                            free(state);
                            free(stack);
                            return false;
                        }
                        if(state[next] == 0) {
                            stack[++top] = next;
                        }
                    }
                } else {
                    state[course] = 2;
                    top--;
                }
            }
        }
    }
    
    // Clean up
    for(int i = 0; i < numCourses; i++) {
        free(adj[i]);
    }
    free(adj);
    free(adjSize);
    free(state);
    free(stack);
    
    return true;
}

66)

a) #include <stdio.h>
#include <stdlib.h>

#define MAX 100

typedef struct {
    int vertices;
    int adjMatrix[MAX][MAX];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            g->adjMatrix[i][j] = 0;
        }
    }
}

void addEdge(Graph* g, int u, int v) {
    g->adjMatrix[u][v] = 1;
}

// Topological Sort using DFS
void topologicalSortDFS(Graph* g, int vertex, int* visited, int* stack, int* stackTop) {
    visited[vertex] = 1;
    
    for(int i = 0; i < g->vertices; i++) {
        if(g->adjMatrix[vertex][i] == 1 && !visited[i]) {
            topologicalSortDFS(g, i, visited, stack, stackTop);
        }
    }
    
    stack[++(*stackTop)] = vertex;
}

void topologicalSort(Graph* g) {
    int visited[MAX] = {0};
    int stack[MAX];
    int stackTop = -1;
    
    for(int i = 0; i < g->vertices; i++) {
        if(!visited[i]) {
            topologicalSortDFS(g, i, visited, stack, &stackTop);
        }
    }
    
    printf("Topological Order: ");
    for(int i = stackTop; i >= 0; i--) {
        printf("%d ", stack[i]);
    }
    printf("\n");
}

// Topological Sort using Kahn's Algorithm (BFS with indegree)
void topologicalSortKahn(Graph* g) {
    int indegree[MAX] = {0};
    int queue[MAX], front = 0, rear = 0;
    int result[MAX], resultSize = 0;
    
    // Calculate indegree
    for(int i = 0; i < g->vertices; i++) {
        for(int j = 0; j < g->vertices; j++) {
            if(g->adjMatrix[i][j] == 1) {
                indegree[j]++;
            }
        }
    }
    
    // Enqueue vertices with indegree 0
    for(int i = 0; i < g->vertices; i++) {
        if(indegree[i] == 0) {
            queue[rear++] = i;
        }
    }
    
    while(front < rear) {
        int vertex = queue[front++];
        result[resultSize++] = vertex;
        
        for(int i = 0; i < g->vertices; i++) {
            if(g->adjMatrix[vertex][i] == 1) {
                indegree[i]--;
                if(indegree[i] == 0) {
                    queue[rear++] = i;
                }
            }
        }
    }
    
    if(resultSize != g->vertices) {
        printf("Graph has a cycle! Topological sort not possible.\n");
        return;
    }
    
    printf("Topological Order (Kahn's): ");
    for(int i = 0; i < resultSize; i++) {
        printf("%d ", result[i]);
    }
    printf("\n");
}

int main() {
    Graph g;
    int vertices, edges, u, v;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    printf("Enter edges (u -> v):\n");
    for(int i = 0; i < edges; i++) {
        printf("Edge %d: ", i + 1);
        scanf("%d %d", &u, &v);
        addEdge(&g, u, v);
    }
    
    topologicalSort(&g);
    topologicalSortKahn(&g);
    
    return 0;
}

b) /**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* findOrder(int numCourses, int** prerequisites, int prerequisitesSize, int* prerequisitesColSize, int* returnSize) {
    // Build adjacency list and indegree array
    int** adj = (int**)malloc(numCourses * sizeof(int*));
    int* adjSize = (int*)calloc(numCourses, sizeof(int));
    int* indegree = (int*)calloc(numCourses, sizeof(int));
    
    for(int i = 0; i < numCourses; i++) {
        adj[i] = (int*)malloc(numCourses * sizeof(int));
    }
    
    for(int i = 0; i < prerequisitesSize; i++) {
        int course = prerequisites[i][0];
        int prereq = prerequisites[i][1];
        adj[prereq][adjSize[prereq]++] = course;
        indegree[course]++;
    }
    
    // Kahn's algorithm
    int* queue = (int*)malloc(numCourses * sizeof(int));
    int front = 0, rear = 0;
    
    for(int i = 0; i < numCourses; i++) {
        if(indegree[i] == 0) {
            queue[rear++] = i;
        }
    }
    
    int* result = (int*)malloc(numCourses * sizeof(int));
    *returnSize = 0;
    
    while(front < rear) {
        int course = queue[front++];
        result[(*returnSize)++] = course;
        
        for(int i = 0; i < adjSize[course]; i++) {
            int next = adj[course][i];
            indegree[next]--;
            if(indegree[next] == 0) {
                queue[rear++] = next;
            }
        }
    }
    
    // Clean up
    for(int i = 0; i < numCourses; i++) {
        free(adj[i]);
    }
    free(adj);
    free(adjSize);
    free(indegree);
    free(queue);
    
    if(*returnSize != numCourses) {
        *returnSize = 0;
        free(result);
        return NULL;
    }
    
    return result;
}

67)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 100

void dfs(char grid[MAX][MAX], int rows, int cols, int r, int c) {
    if(r < 0 || r >= rows || c < 0 || c >= cols || grid[r][c] == '0') {
        return;
    }
    
    grid[r][c] = '0';  // Mark as visited
    
    // Visit all 4 directions
    dfs(grid, rows, cols, r + 1, c);
    dfs(grid, rows, cols, r - 1, c);
    dfs(grid, rows, cols, r, c + 1);
    dfs(grid, rows, cols, r, c - 1);
}

int numIslands(char grid[MAX][MAX], int rows, int cols) {
    int count = 0;
    
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < cols; j++) {
            if(grid[i][j] == '1') {
                count++;
                dfs(grid, rows, cols, i, j);
            }
        }
    }
    
    return count;
}

int main() {
    char grid[MAX][MAX];
    int rows, cols;
    
    printf("Enter number of rows and columns: ");
    scanf("%d %d", &rows, &cols);
    
    printf("Enter grid (0 for water, 1 for land):\n");
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < cols; j++) {
            scanf(" %c", &grid[i][j]);
        }
    }
    
    printf("Number of islands: %d\n", numIslands(grid, rows, cols));
    
    return 0;
}

b) void dfs(char** grid, int rows, int cols, int r, int c) {
    if(r < 0 || r >= rows || c < 0 || c >= cols || grid[r][c] == '0') {
        return;
    }
    
    grid[r][c] = '0';
    
    dfs(grid, rows, cols, r + 1, c);
    dfs(grid, rows, cols, r - 1, c);
    dfs(grid, rows, cols, r, c + 1);
    dfs(grid, rows, cols, r, c - 1);
}

int numIslands(char** grid, int gridSize, int* gridColSize) {
    if(gridSize == 0) return 0;
    
    int count = 0;
    
    for(int i = 0; i < gridSize; i++) {
        for(int j = 0; j < gridColSize[i]; j++) {
            if(grid[i][j] == '1') {
                count++;
                dfs(grid, gridSize, gridColSize[i], i, j);
            }
        }
    }
    
    return count;
}

68)

a) #include <stdio.h>
#include <stdlib.h>

#define MAX 100

void dfs(char board[MAX][MAX], int rows, int cols, int r, int c) {
    if(r < 0 || r >= rows || c < 0 || c >= cols || board[r][c] != 'O') {
        return;
    }
    
    board[r][c] = '#';  // Mark as safe
    
    dfs(board, rows, cols, r + 1, c);
    dfs(board, rows, cols, r - 1, c);
    dfs(board, rows, cols, r, c + 1);
    dfs(board, rows, cols, r, c - 1);
}

void solveSurrounded(char board[MAX][MAX], int rows, int cols) {
    if(rows == 0) return;
    
    // Mark all 'O's on boundary and their connected cells as safe
    for(int i = 0; i < rows; i++) {
        if(board[i][0] == 'O') dfs(board, rows, cols, i, 0);
        if(board[i][cols - 1] == 'O') dfs(board, rows, cols, i, cols - 1);
    }
    
    for(int j = 0; j < cols; j++) {
        if(board[0][j] == 'O') dfs(board, rows, cols, 0, j);
        if(board[rows - 1][j] == 'O') dfs(board, rows, cols, rows - 1, j);
    }
    
    // Convert all remaining 'O' to 'X', and '#' back to 'O'
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < cols; j++) {
            if(board[i][j] == 'O') {
                board[i][j] = 'X';
            } else if(board[i][j] == '#') {
                board[i][j] = 'O';
            }
        }
    }
}

void printBoard(char board[MAX][MAX], int rows, int cols) {
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < cols; j++) {
            printf("%c ", board[i][j]);
        }
        printf("\n");
    }
}

int main() {
    char board[MAX][MAX];
    int rows, cols;
    
    printf("Enter number of rows and columns: ");
    scanf("%d %d", &rows, &cols);
    
    printf("Enter board (X or O):\n");
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < cols; j++) {
            scanf(" %c", &board[i][j]);
        }
    }
    
    printf("\nOriginal Board:\n");
    printBoard(board, rows, cols);
    
    solveSurrounded(board, rows, cols);
    
    printf("\nBoard after solving surrounded regions:\n");
    printBoard(board, rows, cols);
    
    return 0;
}

b) void dfs(char** board, int rows, int cols, int r, int c) {
    if(r < 0 || r >= rows || c < 0 || c >= cols || board[r][c] != 'O') {
        return;
    }
    
    board[r][c] = '#';
    
    dfs(board, rows, cols, r + 1, c);
    dfs(board, rows, cols, r - 1, c);
    dfs(board, rows, cols, r, c + 1);
    dfs(board, rows, cols, r, c - 1);
}

void solve(char** board, int boardSize, int* boardColSize) {
    if(boardSize == 0) return;
    int rows = boardSize;
    int cols = boardColSize[0];
    
    // Mark boundary-connected 'O's
    for(int i = 0; i < rows; i++) {
        if(board[i][0] == 'O') dfs(board, rows, cols, i, 0);
        if(board[i][cols - 1] == 'O') dfs(board, rows, cols, i, cols - 1);
    }
    
    for(int j = 0; j < cols; j++) {
        if(board[0][j] == 'O') dfs(board, rows, cols, 0, j);
        if(board[rows - 1][j] == 'O') dfs(board, rows, cols, rows - 1, j);
    }
    
    // Convert
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < cols; j++) {
            if(board[i][j] == 'O') {
                board[i][j] = 'X';
            } else if(board[i][j] == '#') {
                board[i][j] = 'O';
            }
        }
    }
}

69)

a) #include <stdio.h>
#include <stdlib.h>
#include <limits.h>
#include <stdbool.h>

#define MAX 100

typedef struct {
    int vertices;
    int adjMatrix[MAX][MAX];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            g->adjMatrix[i][j] = (i == j) ? 0 : INT_MAX;
        }
    }
}

void addEdge(Graph* g, int u, int v, int weight) {
    g->adjMatrix[u][v] = weight;
    g->adjMatrix[v][u] = weight;  // For undirected
}

int minDistance(int dist[], bool visited[], int n) {
    int min = INT_MAX, minIndex = -1;
    
    for(int i = 0; i < n; i++) {
        if(!visited[i] && dist[i] <= min) {
            min = dist[i];
            minIndex = i;
        }
    }
    
    return minIndex;
}

void dijkstra(Graph* g, int src) {
    int dist[MAX];
    bool visited[MAX];
    int parent[MAX];
    
    // Initialize
    for(int i = 0; i < g->vertices; i++) {
        dist[i] = INT_MAX;
        visited[i] = false;
        parent[i] = -1;
    }
    
    dist[src] = 0;
    
    for(int count = 0; count < g->vertices - 1; count++) {
        int u = minDistance(dist, visited, g->vertices);
        if(u == -1) break;
        visited[u] = true;
        
        for(int v = 0; v < g->vertices; v++) {
            if(!visited[v] && g->adjMatrix[u][v] != INT_MAX && 
               dist[u] != INT_MAX && dist[u] + g->adjMatrix[u][v] < dist[v]) {
                dist[v] = dist[u] + g->adjMatrix[u][v];
                parent[v] = u;
            }
        }
    }
    
    // Print results
    printf("\nDijkstra's Algorithm Results (Source: %d):\n", src);
    printf("Vertex\tDistance\tPath\n");
    for(int i = 0; i < g->vertices; i++) {
        printf("%d\t%d\t\t", i, dist[i]);
        
        // Print path
        if(dist[i] == INT_MAX) {
            printf("No path\n");
        } else {
            int path[MAX], pathLen = 0;
            int current = i;
            while(current != -1) {
                path[pathLen++] = current;
                current = parent[current];
            }
            for(int j = pathLen - 1; j >= 0; j--) {
                printf("%d", path[j]);
                if(j > 0) printf(" -> ");
            }
            printf("\n");
        }
    }
}

int main() {
    Graph g;
    int vertices, edges, u, v, weight, src;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    printf("Enter edges (u v weight):\n");
    for(int i = 0; i < edges; i++) {
        printf("Edge %d: ", i + 1);
        scanf("%d %d %d", &u, &v, &weight);
        addEdge(&g, u, v, weight);
    }
    
    printf("\nEnter source vertex: ");
    scanf("%d", &src);
    
    dijkstra(&g, src);
    
    return 0;
}

b) #include <limits.h>
#include <stdlib.h>

int networkDelayTime(int** times, int timesSize, int* timesColSize, int n, int k) {
    // Build adjacency matrix
    int** graph = (int**)malloc((n + 1) * sizeof(int*));
    for(int i = 1; i <= n; i++) {
        graph[i] = (int*)malloc((n + 1) * sizeof(int));
        for(int j = 1; j <= n; j++) {
            graph[i][j] = (i == j) ? 0 : INT_MAX;
        }
    }
    
    for(int i = 0; i < timesSize; i++) {
        int u = times[i][0];
        int v = times[i][1];
        int w = times[i][2];
        graph[u][v] = w;
    }
    
    // Dijkstra's algorithm
    int* dist = (int*)malloc((n + 1) * sizeof(int));
    int* visited = (int*)calloc(n + 1, sizeof(int));
    
    for(int i = 1; i <= n; i++) {
        dist[i] = INT_MAX;
    }
    dist[k] = 0;
    
    for(int count = 0; count < n; count++) {
        int u = -1;
        int minDist = INT_MAX;
        
        for(int i = 1; i <= n; i++) {
            if(!visited[i] && dist[i] < minDist) {
                minDist = dist[i];
                u = i;
            }
        }
        
        if(u == -1) break;
        visited[u] = 1;
        
        for(int v = 1; v <= n; v++) {
            if(!visited[v] && graph[u][v] != INT_MAX && 
               dist[u] + graph[u][v] < dist[v]) {
                dist[v] = dist[u] + graph[u][v];
            }
        }
    }
    
    // Find maximum distance
    int maxDist = 0;
    for(int i = 1; i <= n; i++) {
        if(dist[i] == INT_MAX) {
            maxDist = -1;
            break;
        }
        if(dist[i] > maxDist) {
            maxDist = dist[i];
        }
    }
    
    // Clean up
    for(int i = 1; i <= n; i++) {
        free(graph[i]);
    }
    free(graph);
    free(dist);
    free(visited);
    
    return maxDist;
}

70)

a) #include <stdio.h>
#include <stdlib.h>
#include <limits.h>

#define MAX_EDGES 1000
#define MAX_VERTICES 100

typedef struct {
    int u, v, weight;
} Edge;

typedef struct {
    int vertices;
    int edges;
    Edge edgeList[MAX_EDGES];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    g->edges = 0;
}

void addEdge(Graph* g, int u, int v, int weight) {
    g->edgeList[g->edges].u = u;
    g->edgeList[g->edges].v = v;
    g->edgeList[g->edges].weight = weight;
    g->edges++;
}

void bellmanFord(Graph* g, int src) {
    int dist[MAX_VERTICES];
    int parent[MAX_VERTICES];
    
    // Initialize distances
    for(int i = 0; i < g->vertices; i++) {
        dist[i] = INT_MAX;
        parent[i] = -1;
    }
    dist[src] = 0;
    
    // Relax edges |V| - 1 times
    for(int i = 1; i <= g->vertices - 1; i++) {
        for(int j = 0; j < g->edges; j++) {
            int u = g->edgeList[j].u;
            int v = g->edgeList[j].v;
            int w = g->edgeList[j].weight;
            
            if(dist[u] != INT_MAX && dist[u] + w < dist[v]) {
                dist[v] = dist[u] + w;
                parent[v] = u;
            }
        }
    }
    
    // Check for negative weight cycles
    int hasNegativeCycle = 0;
    for(int j = 0; j < g->edges; j++) {
        int u = g->edgeList[j].u;
        int v = g->edgeList[j].v;
        int w = g->edgeList[j].weight;
        
        if(dist[u] != INT_MAX && dist[u] + w < dist[v]) {
            hasNegativeCycle = 1;
            break;
        }
    }
    
    // Print results
    printf("\nBellman-Ford Algorithm Results (Source: %d):\n", src);
    
    if(hasNegativeCycle) {
        printf("Graph contains a negative weight cycle!\n");
        return;
    }
    
    printf("Vertex\tDistance\tPath\n");
    for(int i = 0; i < g->vertices; i++) {
        if(dist[i] == INT_MAX) {
            printf("%d\tINF\t\tNo path\n", i);
        } else {
            printf("%d\t%d\t\t", i, dist[i]);
            
            // Print path
            int path[MAX_VERTICES], pathLen = 0;
            int current = i;
            while(current != -1) {
                path[pathLen++] = current;
                current = parent[current];
            }
            for(int j = pathLen - 1; j >= 0; j--) {
                printf("%d", path[j]);
                if(j > 0) printf(" -> ");
            }
            printf("\n");
        }
    }
}

int main() {
    Graph g;
    int vertices, edges, u, v, weight, src;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    printf("Enter edges (u v weight):\n");
    for(int i = 0; i < edges; i++) {
        printf("Edge %d: ", i + 1);
        scanf("%d %d %d", &u, &v, &weight);
        addEdge(&g, u, v, weight);
    }
    
    printf("\nEnter source vertex: ");
    scanf("%d", &src);
    
    bellmanFord(&g, src);
    
    return 0;
}

b) #include <stdlib.h>
#include <limits.h>

int findCheapestPrice(int n, int** flights, int flightsSize, int* flightsColSize, int src, int dst, int k) {
    int* dist = (int*)malloc(n * sizeof(int));
    int* temp = (int*)malloc(n * sizeof(int));
    
    for(int i = 0; i < n; i++) {
        dist[i] = INT_MAX;
    }
    dist[src] = 0;
    
    // Run Bellman-Ford for k+1 iterations
    for(int i = 0; i <= k; i++) {
        // Copy current distances to temp
        for(int j = 0; j < n; j++) {
            temp[j] = dist[j];
        }
        
        // Relax all edges
        for(int j = 0; j < flightsSize; j++) {
            int u = flights[j][0];
            int v = flights[j][1];
            int w = flights[j][2];
            
            if(dist[u] != INT_MAX && dist[u] + w < temp[v]) {
                temp[v] = dist[u] + w;
            }
        }
        
        // Update distances
        for(int j = 0; j < n; j++) {
            dist[j] = temp[j];
        }
    }
    
    int result = (dist[dst] == INT_MAX) ? -1 : dist[dst];
    
    free(dist);
    free(temp);
    
    return result;
}

71)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define TABLE_SIZE 11
#define EMPTY -1
#define DELETED -2

typedef struct {
    int* table;
    int size;
    int count;
} HashTable;

// Initialize hash table
HashTable* createHashTable(int size) {
    HashTable* ht = (HashTable*)malloc(sizeof(HashTable));
    ht->table = (int*)malloc(size * sizeof(int));
    ht->size = size;
    ht->count = 0;
    
    for(int i = 0; i < size; i++) {
        ht->table[i] = EMPTY;
    }
    
    return ht;
}

// Hash function
int hash(int key, int size) {
    return key % size;
}

// Quadratic probing insert
void insertQuadratic(HashTable* ht, int key) {
    if(ht->count >= ht->size) {
        printf("Hash table is full! Cannot insert %d\n", key);
        return;
    }
    
    int index = hash(key, ht->size);
    int i = 0;
    
    // Quadratic probing
    while(ht->table[(index + i * i) % ht->size] != EMPTY && 
          ht->table[(index + i * i) % ht->size] != DELETED) {
        i++;
        if(i > ht->size) {
            printf("Cannot insert %d - table full\n", key);
            return;
        }
    }
    
    int finalIndex = (index + i * i) % ht->size;
    ht->table[finalIndex] = key;
    ht->count++;
    printf("Inserted %d at index %d\n", key, finalIndex);
}

// Search using quadratic probing
int searchQuadratic(HashTable* ht, int key) {
    int index = hash(key, ht->size);
    int i = 0;
    
    while(ht->table[(index + i * i) % ht->size] != EMPTY) {
        int currentIndex = (index + i * i) % ht->size;
        if(ht->table[currentIndex] == key) {
            return currentIndex;
        }
        i++;
        if(i > ht->size) break;
    }
    
    return -1;
}

// Delete using quadratic probing (lazy deletion)
void deleteQuadratic(HashTable* ht, int key) {
    int index = searchQuadratic(ht, key);
    if(index != -1) {
        ht->table[index] = DELETED;
        ht->count--;
        printf("Deleted %d from index %d\n", key, index);
    } else {
        printf("Key %d not found\n", key);
    }
}

// Linear probing insert (for comparison)
void insertLinear(HashTable* ht, int key) {
    if(ht->count >= ht->size) {
        printf("Hash table is full!\n");
        return;
    }
    
    int index = hash(key, ht->size);
    
    while(ht->table[index] != EMPTY && ht->table[index] != DELETED) {
        index = (index + 1) % ht->size;
    }
    
    ht->table[index] = key;
    ht->count++;
    printf("Inserted %d at index %d (Linear)\n", key, index);
}

// Display hash table
void displayHashTable(HashTable* ht) {
    printf("\nHash Table:\n");
    printf("Index\tValue\n");
    for(int i = 0; i < ht->size; i++) {
        if(ht->table[i] == EMPTY) {
            printf("%d\tEMPTY\n", i);
        } else if(ht->table[i] == DELETED) {
            printf("%d\tDELETED\n", i);
        } else {
            printf("%d\t%d\n", i, ht->table[i]);
        }
    }
}

int main() {
    HashTable* ht = createHashTable(TABLE_SIZE);
    int choice, key, probingType;
    
    printf("Choose probing method:\n");
    printf("1. Quadratic Probing\n");
    printf("2. Linear Probing\n");
    printf("Enter choice: ");
    scanf("%d", &probingType);
    
    while(1) {
        printf("\n--- Hash Table Menu ---\n");
        printf("1. Insert\n");
        printf("2. Search\n");
        printf("3. Delete\n");
        printf("4. Display\n");
        printf("5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        
        switch(choice) {
            case 1:
                printf("Enter key to insert: ");
                scanf("%d", &key);
                if(probingType == 1) {
                    insertQuadratic(ht, key);
                } else {
                    insertLinear(ht, key);
                }
                break;
            case 2:
                printf("Enter key to search: ");
                scanf("%d", &key);
                int idx = searchQuadratic(ht, key);
                if(idx != -1) {
                    printf("Key %d found at index %d\n", key, idx);
                } else {
                    printf("Key %d not found\n", key);
                }
                break;
            case 3:
                printf("Enter key to delete: ");
                scanf("%d", &key);
                deleteQuadratic(ht, key);
                break;
            case 4:
                displayHashTable(ht);
                break;
            case 5:
                printf("Exiting...\n");
                free(ht->table);
                free(ht);
                return 0;
            default:
                printf("Invalid choice!\n");
        }
    }
    
    return 0;
}

b) #include <stdio.h>
#include <limits.h>
#include <stdbool.h>

#define MAX 10

int tsp(int graph[MAX][MAX], int n, int start) {
    int vertices[MAX];
    for(int i = 0; i < n; i++) {
        vertices[i] = i;
    }
    
    // Simple brute force (for small n)
    int minCost = INT_MAX;
    
    // Generate all permutations (simplified - using recursion)
    // This is a simplified version
    
    // For a proper TSP solution, use Held-Karp DP:
    // dp[mask][i] = min cost to visit all cities in mask ending at i
    
    int dp[1 << MAX][MAX];
    for(int i = 0; i < (1 << n); i++) {
        for(int j = 0; j < n; j++) {
            dp[i][j] = INT_MAX;
        }
    }
    
    dp[1 << start][start] = 0;
    
    for(int mask = 1; mask < (1 << n); mask++) {
        for(int u = 0; u < n; u++) {
            if(dp[mask][u] != INT_MAX) {
                for(int v = 0; v < n; v++) {
                    if(!(mask & (1 << v)) && graph[u][v] != 0) {
                        int newMask = mask | (1 << v);
                        int newCost = dp[mask][u] + graph[u][v];
                        if(newCost < dp[newMask][v]) {
                            dp[newMask][v] = newCost;
                        }
                    }
                }
            }
        }
    }
    
    int finalMask = (1 << n) - 1;
    for(int v = 0; v < n; v++) {
        if(dp[finalMask][v] != INT_MAX && graph[v][start] != 0) {
            int total = dp[finalMask][v] + graph[v][start];
            if(total < minCost) {
                minCost = total;
            }
        }
    }
    
    return minCost;
}

int main() {
    int graph[MAX][MAX], n;
    
    printf("Enter number of cities: ");
    scanf("%d", &n);
    
    printf("Enter adjacency matrix (0 for no edge):\n");
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            scanf("%d", &graph[i][j]);
        }
    }
    
    int start = 0;
    int minCost = tsp(graph, n, start);
    
    printf("Minimum TSP cost: %d\n", minCost);
    
    return 0;
}

72)

a) #include <stdio.h>
#include <string.h>
#include <limits.h>

#define MAX_CHAR 256

// Find first character that repeats
char firstRepeatedChar(char* str) {
    int count[MAX_CHAR] = {0};
    
    for(int i = 0; str[i] != '\0'; i++) {
        count[(int)str[i]]++;
    }
    
    for(int i = 0; str[i] != '\0'; i++) {
        if(count[(int)str[i]] > 1) {
            return str[i];
        }
    }
    
    return '\0';
}

// Find first non-repeating character
char firstNonRepeatingChar(char* str) {
    int count[MAX_CHAR] = {0};
    
    for(int i = 0; str[i] != '\0'; i++) {
        count[(int)str[i]]++;
    }
    
    for(int i = 0; str[i] != '\0'; i++) {
        if(count[(int)str[i]] == 1) {
            return str[i];
        }
    }
    
    return '\0';
}

// Find index of first repeated character
int firstRepeatedIndex(char* str) {
    int firstIndex[MAX_CHAR];
    for(int i = 0; i < MAX_CHAR; i++) {
        firstIndex[i] = -1;
    }
    
    int minIndex = INT_MAX;
    
    for(int i = 0; str[i] != '\0'; i++) {
        if(firstIndex[(int)str[i]] == -1) {
            firstIndex[(int)str[i]] = i;
        } else {
            if(firstIndex[(int)str[i]] < minIndex) {
                minIndex = firstIndex[(int)str[i]];
            }
        }
    }
    
    return minIndex;
}

int main() {
    char str[100];
    
    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';
    
    char repeated = firstRepeatedChar(str);
    if(repeated != '\0') {
        printf("First repeated character: '%c'\n", repeated);
    } else {
        printf("No repeated character found\n");
    }
    
    char nonRepeated = firstNonRepeatingChar(str);
    if(nonRepeated != '\0') {
        printf("First non-repeating character: '%c'\n", nonRepeated);
    } else {
        printf("No non-repeating character found\n");
    }
    
    int idx = firstRepeatedIndex(str);
    if(idx != INT_MAX) {
        printf("Index of first repeated character: %d\n", idx);
    }
    
    return 0;
}

b) // Already covered in Day 61, but here's a review:

typedef struct {
    int vertices;
    int** matrix;
} Graph;

Graph* createGraph(int vertices) {
    Graph* g = (Graph*)malloc(sizeof(Graph));
    g->vertices = vertices;
    g->matrix = (int**)malloc(vertices * sizeof(int*));
    for(int i = 0; i < vertices; i++) {
        g->matrix[i] = (int*)calloc(vertices, sizeof(int));
    }
    return g;
}

void addEdge(Graph* g, int u, int v) {
    g->matrix[u][v] = 1;
    g->matrix[v][u] = 1;  // For undirected
}

void printGraph(Graph* g) {
    for(int i = 0; i < g->vertices; i++) {
        for(int j = 0; j < g->vertices; j++) {
            printf("%d ", g->matrix[i][j]);
        }
        printf("\n");
    }
}

73)

a) #include <stdio.h>
#include <string.h>
#include <limits.h>

#define MAX_CHAR 256

int longestUniqueSubstring(char* str) {
    int lastIndex[MAX_CHAR];
    for(int i = 0; i < MAX_CHAR; i++) {
        lastIndex[i] = -1;
    }
    
    int maxLen = 0;
    int start = 0;
    int n = strlen(str);
    
    for(int end = 0; end < n; end++) {
        char ch = str[end];
        
        if(lastIndex[(int)ch] >= start) {
            start = lastIndex[(int)ch] + 1;
        }
        
        lastIndex[(int)ch] = end;
        int currentLen = end - start + 1;
        if(currentLen > maxLen) {
            maxLen = currentLen;
        }
    }
    
    return maxLen;
}

// Print the longest substring
void printLongestUniqueSubstring(char* str) {
    int lastIndex[MAX_CHAR];
    for(int i = 0; i < MAX_CHAR; i++) {
        lastIndex[i] = -1;
    }
    
    int maxLen = 0;
    int start = 0;
    int maxStart = 0;
    int n = strlen(str);
    
    for(int end = 0; end < n; end++) {
        char ch = str[end];
        
        if(lastIndex[(int)ch] >= start) {
            start = lastIndex[(int)ch] + 1;
        }
        
        lastIndex[(int)ch] = end;
        int currentLen = end - start + 1;
        if(currentLen > maxLen) {
            maxLen = currentLen;
            maxStart = start;
        }
    }
    
    printf("Longest substring without repeating: ");
    for(int i = maxStart; i < maxStart + maxLen; i++) {
        printf("%c", str[i]);
    }
    printf("\nLength: %d\n", maxLen);
}

int main() {
    char str[100];
    
    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';
    
    printLongestUniqueSubstring(str);
    
    return 0;
}

b) int lengthOfLongestSubstring(char* s) {
    int lastIndex[128];
    for(int i = 0; i < 128; i++) {
        lastIndex[i] = -1;
    }
    
    int maxLen = 0;
    int start = 0;
    int n = strlen(s);
    
    for(int end = 0; end < n; end++) {
        char ch = s[end];
        
        if(lastIndex[(int)ch] >= start) {
            start = lastIndex[(int)ch] + 1;
        }
        
        lastIndex[(int)ch] = end;
        int currentLen = end - start + 1;
        if(currentLen > maxLen) {
            maxLen = currentLen;
        }
    }
    
    return maxLen;
}

74)

a) #include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX_VOTES 100
#define MAX_NAME 50

typedef struct {
    char name[MAX_NAME];
    int votes;
} Candidate;

int findCandidate(Candidate candidates[], int count, char* name) {
    for(int i = 0; i < count; i++) {
        if(strcmp(candidates[i].name, name) == 0) {
            return i;
        }
    }
    return -1;
}

void findWinner(char* votes[], int n) {
    Candidate candidates[MAX_VOTES];
    int candidateCount = 0;
    
    for(int i = 0; i < n; i++) {
        int idx = findCandidate(candidates, candidateCount, votes[i]);
        if(idx == -1) {
            strcpy(candidates[candidateCount].name, votes[i]);
            candidates[candidateCount].votes = 1;
            candidateCount++;
        } else {
            candidates[idx].votes++;
        }
    }
    
    // Find winner
    int maxVotes = 0;
    int winnerIndex = 0;
    for(int i = 0; i < candidateCount; i++) {
        if(candidates[i].votes > maxVotes) {
            maxVotes = candidates[i].votes;
            winnerIndex = i;
        } else if(candidates[i].votes == maxVotes) {
            // Tie - choose lexicographically smaller
            if(strcmp(candidates[i].name, candidates[winnerIndex].name) < 0) {
                winnerIndex = i;
            }
        }
    }
    
    printf("Winner: %s\n", candidates[winnerIndex].name);
    printf("Votes: %d\n", maxVotes);
}

int main() {
    char* votes[] = {"john", "johnny", "jackie", "johnny", "john", "jackie", "jamie", "jamie", "john", "johnny", "jamie", "johnny", "john"};
    int n = sizeof(votes) / sizeof(votes[0]);
    
    findWinner(votes, n);
    
    return 0;
}

b) void dfs(int** adj, int* adjSize, int node, int* visited) {
    visited[node] = 1;
    
    for(int i = 0; i < adjSize[node]; i++) {
        int neighbor = adj[node][i];
        if(!visited[neighbor]) {
            dfs(adj, adjSize, neighbor, visited);
        }
    }
}

int countComponents(int n, int** edges, int edgesSize, int* edgesColSize) {
    // Build adjacency list
    int** adj = (int**)malloc(n * sizeof(int*));
    int* adjSize = (int*)calloc(n, sizeof(int));
    
    for(int i = 0; i < n; i++) {
        adj[i] = (int*)malloc(n * sizeof(int));
    }
    
    for(int i = 0; i < edgesSize; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        adj[u][adjSize[u]++] = v;
        adj[v][adjSize[v]++] = u;
    }
    
    int* visited = (int*)calloc(n, sizeof(int));
    int components = 0;
    
    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            components++;
            dfs(adj, adjSize, i, visited);
        }
    }
    
    // Cleanup
    for(int i = 0; i < n; i++) {
        free(adj[i]);
    }
    free(adj);
    free(adjSize);
    free(visited);
    
    return components;
}

75)

a) #include <stdio.h>
#include <stdlib.h>

#define MAX 100

int max(int a, int b) {
    return (a > b) ? a : b;
}

int largestSubarrayWithZeroSum(int arr[], int n) {
    int maxLen = 0;
    int prefixSum = 0;
    
    // Simple approach: O(n²)
    for(int i = 0; i < n; i++) {
        prefixSum = 0;
        for(int j = i; j < n; j++) {
            prefixSum += arr[j];
            if(prefixSum == 0) {
                maxLen = max(maxLen, j - i + 1);
            }
        }
    }
    
    return maxLen;
}

// Optimized using hash map (simulated with array for small ranges)
int largestSubarrayWithZeroSumOptimized(int arr[], int n) {
    int maxLen = 0;
    int prefixSum = 0;
    int hashMap[MAX * 2 + 1];  // For small range values
    
    for(int i = 0; i < MAX * 2 + 1; i++) {
        hashMap[i] = -2;  // -2 means not seen
    }
    
    hashMap[MAX] = -1;  // For sum 0 at index -1
    
    for(int i = 0; i < n; i++) {
        prefixSum += arr[i];
        int index = prefixSum + MAX;
        
        if(hashMap[index] != -2) {
            maxLen = max(maxLen, i - hashMap[index]);
        } else {
            hashMap[index] = i;
        }
    }
    
    return maxLen;
}

int main() {
    int arr[MAX], n;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    int result = largestSubarrayWithZeroSum(arr, n);
    printf("Largest subarray with zero sum length: %d\n", result);
    
    return 0;
}

b) #include <stdbool.h>
#include <stdlib.h>

bool isBipartite(int** graph, int graphSize, int* graphColSize) {
    int* color = (int*)calloc(graphSize, sizeof(int));  // 0 = uncolored, 1 = red, -1 = blue
    
    for(int i = 0; i < graphSize; i++) {
        if(color[i] == 0) {
            // BFS
            int* queue = (int*)malloc(graphSize * sizeof(int));
            int front = 0, rear = 0;
            
            color[i] = 1;
            queue[rear++] = i;
            
            while(front < rear) {
                int node = queue[front++];
                
                for(int j = 0; j < graphColSize[node]; j++) {
                    int neighbor = graph[node][j];
                    
                    if(color[neighbor] == 0) {
                        color[neighbor] = -color[node];
                        queue[rear++] = neighbor;
                    } else if(color[neighbor] == color[node]) {
                        free(queue);
                        free(color);
                        return false;
                    }
                }
            }
            free(queue);
        }
    }
    
    free(color);
    return true;
}

76)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 100

typedef struct {
    int vertices;
    int adjMatrix[MAX][MAX];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            g->adjMatrix[i][j] = 0;
        }
    }
}

void addEdge(Graph* g, int u, int v) {
    g->adjMatrix[u][v] = 1;
    g->adjMatrix[v][u] = 1;
}

void dfs(Graph* g, int vertex, bool* visited) {
    visited[vertex] = true;
    
    for(int i = 0; i < g->vertices; i++) {
        if(g->adjMatrix[vertex][i] == 1 && !visited[i]) {
            dfs(g, i, visited);
        }
    }
}

int countConnectedComponents(Graph* g) {
    bool visited[MAX] = {false};
    int count = 0;
    
    for(int i = 0; i < g->vertices; i++) {
        if(!visited[i]) {
            count++;
            dfs(g, i, visited);
        }
    }
    
    return count;
}

void printComponents(Graph* g) {
    bool visited[MAX] = {false};
    int componentNum = 0;
    
    for(int i = 0; i < g->vertices; i++) {
        if(!visited[i]) {
            componentNum++;
            printf("Component %d: ", componentNum);
            
            // DFS to print component
            int stack[MAX], top = -1;
            stack[++top] = i;
            
            while(top >= 0) {
                int vertex = stack[top--];
                if(!visited[vertex]) {
                    visited[vertex] = true;
                    printf("%d ", vertex);
                    
                    for(int j = g->vertices - 1; j >= 0; j--) {
                        if(g->adjMatrix[vertex][j] == 1 && !visited[j]) {
                            stack[++top] = j;
                        }
                    }
                }
            }
            printf("\n");
        }
    }
}

int main() {
    Graph g;
    int vertices, edges, u, v;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    for(int i = 0; i < edges; i++) {
        printf("Edge %d (u v): ", i + 1);
        scanf("%d %d", &u, &v);
        addEdge(&g, u, v);
    }
    
    printComponents(&g);
    printf("Total connected components: %d\n", countConnectedComponents(&g));
    
    return 0;
}

b) /**
 * Definition for a Node.
 * struct Node {
 *     int val;
 *     int numNeighbors;
 *     struct Node** neighbors;
 * };
 */

struct Node* dfs(struct Node* node, struct Node** visited) {
    if(node == NULL) return NULL;
    
    if(visited[node->val] != NULL) {
        return visited[node->val];
    }
    
    struct Node* clone = (struct Node*)malloc(sizeof(struct Node));
    clone->val = node->val;
    clone->numNeighbors = node->numNeighbors;
    clone->neighbors = (struct Node**)malloc(node->numNeighbors * sizeof(struct Node*));
    
    visited[node->val] = clone;
    
    for(int i = 0; i < node->numNeighbors; i++) {
        clone->neighbors[i] = dfs(node->neighbors[i], visited);
    }
    
    return clone;
}

struct Node* cloneGraph(struct Node* s) {
    struct Node** visited = (struct Node**)calloc(101, sizeof(struct Node*));
    return dfs(s, visited);
}

77)

a) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 100

typedef struct {
    int vertices;
    int adjMatrix[MAX][MAX];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            g->adjMatrix[i][j] = 0;
        }
    }
}

void addEdge(Graph* g, int u, int v) {
    g->adjMatrix[u][v] = 1;
    g->adjMatrix[v][u] = 1;
}

void bfs(Graph* g, int start, bool* visited) {
    int queue[MAX], front = 0, rear = 0;
    
    visited[start] = true;
    queue[rear++] = start;
    
    while(front < rear) {
        int vertex = queue[front++];
        
        for(int i = 0; i < g->vertices; i++) {
            if(g->adjMatrix[vertex][i] == 1 && !visited[i]) {
                visited[i] = true;
                queue[rear++] = i;
            }
        }
    }
}

bool isConnected(Graph* g) {
    bool visited[MAX] = {false};
    
    bfs(g, 0, visited);
    
    for(int i = 0; i < g->vertices; i++) {
        if(!visited[i]) {
            return false;
        }
    }
    return true;
}

// Find articulation points (Tarjan's algorithm)
int time = 0;
void findArticulationPointsUtil(Graph* g, int u, bool* visited, int* disc, int* low, int* parent, bool* ap) {
    int children = 0;
    visited[u] = true;
    disc[u] = low[u] = ++time;
    
    for(int v = 0; v < g->vertices; v++) {
        if(g->adjMatrix[u][v] == 1) {
            if(!visited[v]) {
                children++;
                parent[v] = u;
                findArticulationPointsUtil(g, v, visited, disc, low, parent, ap);
                
                low[u] = (low[u] < low[v]) ? low[u] : low[v];
                
                if(parent[u] == -1 && children > 1) {
                    ap[u] = true;
                }
                if(parent[u] != -1 && low[v] >= disc[u]) {
                    ap[u] = true;
                }
            } else if(v != parent[u]) {
                low[u] = (low[u] < disc[v]) ? low[u] : disc[v];
            }
        }
    }
}

void findArticulationPoints(Graph* g) {
    bool visited[MAX] = {false};
    int disc[MAX], low[MAX], parent[MAX];
    bool ap[MAX] = {false};
    
    for(int i = 0; i < g->vertices; i++) {
        parent[i] = -1;
    }
    
    for(int i = 0; i < g->vertices; i++) {
        if(!visited[i]) {
            findArticulationPointsUtil(g, i, visited, disc, low, parent, ap);
        }
    }
    
    printf("Articulation Points: ");
    for(int i = 0; i < g->vertices; i++) {
        if(ap[i]) {
            printf("%d ", i);
        }
    }
    printf("\n");
}

int main() {
    Graph g;
    int vertices, edges, u, v;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    for(int i = 0; i < edges; i++) {
        printf("Edge %d (u v): ", i + 1);
        scanf("%d %d", &u, &v);
        addEdge(&g, u, v);
    }
    
    if(isConnected(&g)) {
        printf("Graph is connected\n");
    } else {
        printf("Graph is NOT connected\n");
    }
    
    findArticulationPoints(&g);
    
    return 0;
}

b) /**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int time = 0;

void dfs(int node, int parent, int** adj, int* adjSize, int* disc, int* low, int** result, int* returnSize, int* visited) {
    visited[node] = 1;
    disc[node] = low[node] = ++time;
    
    for(int i = 0; i < adjSize[node]; i++) {
        int neighbor = adj[node][i];
        
        if(neighbor == parent) continue;
        
        if(!visited[neighbor]) {
            dfs(neighbor, node, adj, adjSize, disc, low, result, returnSize, visited);
            low[node] = (low[node] < low[neighbor]) ? low[node] : low[neighbor];
            
            if(low[neighbor] > disc[node]) {
                // Critical connection found
                result[*returnSize] = (int*)malloc(2 * sizeof(int));
                result[*returnSize][0] = node;
                result[*returnSize][1] = neighbor;
                (*returnSize)++;
            }
        } else {
            low[node] = (low[node] < disc[neighbor]) ? low[node] : disc[neighbor];
        }
    }
}

int** criticalConnections(int n, int** connections, int connectionsSize, int* connectionsColSize, int* returnSize) {
    // Build adjacency list
    int** adj = (int**)malloc(n * sizeof(int*));
    int* adjSize = (int*)calloc(n, sizeof(int));
    
    for(int i = 0; i < n; i++) {
        adj[i] = (int*)malloc(n * sizeof(int));
    }
    
    for(int i = 0; i < connectionsSize; i++) {
        int u = connections[i][0];
        int v = connections[i][1];
        adj[u][adjSize[u]++] = v;
        adj[v][adjSize[v]++] = u;
    }
    
    int* disc = (int*)calloc(n, sizeof(int));
    int* low = (int*)calloc(n, sizeof(int));
    int* visited = (int*)calloc(n, sizeof(int));
    int** result = (int**)malloc(n * n * sizeof(int*));
    *returnSize = 0;
    time = 0;
    
    dfs(0, -1, adj, adjSize, disc, low, result, returnSize, visited);
    
    // Cleanup
    for(int i = 0; i < n; i++) {
        free(adj[i]);
    }
    free(adj);
    free(adjSize);
    free(disc);
    free(low);
    free(visited);
    
    return result;
}

78)

a) #include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>

#define MAX_WORDS 5000
#define MAX_LEN 10

typedef struct {
    char word[MAX_LEN];
    int distance;
} QueueNode;

bool isAdjacent(char* a, char* b) {
    int diff = 0;
    int len = strlen(a);
    for(int i = 0; i < len; i++) {
        if(a[i] != b[i]) {
            diff++;
            if(diff > 1) return false;
        }
    }
    return diff == 1;
}

int ladderLength(char* beginWord, char* endWord, char** wordList, int wordListSize) {
    bool* visited = (bool*)calloc(wordListSize, sizeof(bool));
    
    QueueNode queue[MAX_WORDS];
    int front = 0, rear = 0;
    
    strcpy(queue[rear].word, beginWord);
    queue[rear].distance = 1;
    rear++;
    
    while(front < rear) {
        QueueNode current = queue[front++];
        
        for(int i = 0; i < wordListSize; i++) {
            if(!visited[i] && isAdjacent(current.word, wordList[i])) {
                if(strcmp(wordList[i], endWord) == 0) {
                    free(visited);
                    return current.distance + 1;
                }
                visited[i] = true;
                strcpy(queue[rear].word, wordList[i]);
                queue[rear].distance = current.distance + 1;
                rear++;
            }
        }
    }
    
    free(visited);
    return 0;
}

int main() {
    char beginWord[] = "hit";
    char endWord[] = "cog";
    char* wordList[] = {"hot", "dot", "dog", "lot", "log", "cog"};
    int wordListSize = 6;
    
    int result = ladderLength(beginWord, endWord, wordList, wordListSize);
    printf("Shortest transformation length: %d\n", result);
    
    return 0;
}

b) int ladderLength(char* beginWord, char* endWord, char** wordList, int wordListSize) {
    // Similar implementation as above
    // Using queue for BFS
    // Returns minimum number of steps
}

79)

a) // Already covered in Day 69, here's a review with adjacency list:

#include <stdio.h>
#include <stdlib.h>
#include <limits.h>
#include <stdbool.h>

#define MAX 100

typedef struct Edge {
    int dest;
    int weight;
    struct Edge* next;
} Edge;

typedef struct {
    Edge* head;
} AdjList;

typedef struct {
    int vertices;
    AdjList array[MAX];
} Graph;

void addEdge(Graph* g, int src, int dest, int weight) {
    Edge* newEdge = (Edge*)malloc(sizeof(Edge));
    newEdge->dest = dest;
    newEdge->weight = weight;
    newEdge->next = g->array[src].head;
    g->array[src].head = newEdge;
}

void dijkstra(Graph* g, int src) {
    int dist[MAX];
    bool visited[MAX];
    int parent[MAX];
    
    for(int i = 0; i < g->vertices; i++) {
        dist[i] = INT_MAX;
        visited[i] = false;
        parent[i] = -1;
    }
    
    dist[src] = 0;
    
    for(int count = 0; count < g->vertices - 1; count++) {
        int minDist = INT_MAX, u = -1;
        for(int i = 0; i < g->vertices; i++) {
            if(!visited[i] && dist[i] < minDist) {
                minDist = dist[i];
                u = i;
            }
        }
        
        if(u == -1) break;
        visited[u] = true;
        
        Edge* edge = g->array[u].head;
        while(edge != NULL) {
            int v = edge->dest;
            int weight = edge->weight;
            
            if(!visited[v] && dist[u] != INT_MAX && dist[u] + weight < dist[v]) {
                dist[v] = dist[u] + weight;
                parent[v] = u;
            }
            edge = edge->next;
        }
    }
    
    printf("Vertex\tDistance\tPath\n");
    for(int i = 0; i < g->vertices; i++) {
        printf("%d\t%d\t\t", i, dist[i]);
        // Print path...
        printf("\n");
    }
}

b) #include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX 100

typedef struct {
    int vertices;
    int adjMatrix[MAX][MAX];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            g->adjMatrix[i][j] = 0;
        }
    }
}

void addEdge(Graph* g, int u, int v) {
    g->adjMatrix[u][v] = 1;
}

void fillOrder(Graph* g, int v, bool* visited, int* stack, int* stackTop) {
    visited[v] = true;
    
    for(int i = 0; i < g->vertices; i++) {
        if(g->adjMatrix[v][i] == 1 && !visited[i]) {
            fillOrder(g, i, visited, stack, stackTop);
        }
    }
    
    stack[++(*stackTop)] = v;
}

Graph* getTranspose(Graph* g) {
    Graph* transpose = (Graph*)malloc(sizeof(Graph));
    initGraph(transpose, g->vertices);
    
    for(int i = 0; i < g->vertices; i++) {
        for(int j = 0; j < g->vertices; j++) {
            if(g->adjMatrix[i][j] == 1) {
                transpose->adjMatrix[j][i] = 1;
            }
        }
    }
    
    return transpose;
}

void dfsUtil(Graph* g, int v, bool* visited) {
    visited[v] = true;
    printf("%d ", v);
    
    for(int i = 0; i < g->vertices; i++) {
        if(g->adjMatrix[v][i] == 1 && !visited[i]) {
            dfsUtil(g, i, visited);
        }
    }
}

void kosarajuSCC(Graph* g) {
    int stack[MAX], stackTop = -1;
    bool visited[MAX] = {false};
    
    // Step 1: Fill vertices in stack according to finish time
    for(int i = 0; i < g->vertices; i++) {
        if(!visited[i]) {
            fillOrder(g, i, visited, stack, &stackTop);
        }
    }
    
    // Step 2: Get transpose of graph
    Graph* transpose = getTranspose(g);
    
    // Step 3: Process vertices in stack order
    for(int i = 0; i < g->vertices; i++) {
        visited[i] = false;
    }
    
    printf("Strongly Connected Components:\n");
    int componentNum = 0;
    
    while(stackTop >= 0) {
        int v = stack[stackTop--];
        
        if(!visited[v]) {
            componentNum++;
            printf("Component %d: ", componentNum);
            dfsUtil(transpose, v, visited);
            printf("\n");
        }
    }
    
    free(transpose);
}

int main() {
    Graph g;
    int vertices, edges, u, v;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    for(int i = 0; i < edges; i++) {
        printf("Edge %d (u -> v): ", i + 1);
        scanf("%d %d", &u, &v);
        addEdge(&g, u, v);
    }
    
    kosarajuSCC(&g);
    
    return 0;
}

80)

a) #include <stdio.h>
#include <stdlib.h>
#include <limits.h>

#define MAX 100
#define INF 99999

typedef struct {
    int vertices;
    int dist[MAX][MAX];
} Graph;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    for(int i = 0; i < vertices; i++) {
        for(int j = 0; j < vertices; j++) {
            if(i == j) {
                g->dist[i][j] = 0;
            } else {
                g->dist[i][j] = INF;
            }
        }
    }
}

void addEdge(Graph* g, int u, int v, int weight) {
    g->dist[u][v] = weight;
}

void floydWarshall(Graph* g) {
    int n = g->vertices;
    int dist[MAX][MAX];
    int next[MAX][MAX];
    
    // Initialize distance matrix
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            dist[i][j] = g->dist[i][j];
            if(g->dist[i][j] != INF && i != j) {
                next[i][j] = j;
            } else {
                next[i][j] = -1;
            }
        }
    }
    
    // Floyd-Warshall algorithm
    for(int k = 0; k < n; k++) {
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < n; j++) {
                if(dist[i][k] != INF && dist[k][j] != INF && 
                   dist[i][k] + dist[k][j] < dist[i][j]) {
                    dist[i][j] = dist[i][k] + dist[k][j];
                    next[i][j] = next[i][k];
                }
            }
        }
    }
    
    // Check for negative cycles
    for(int i = 0; i < n; i++) {
        if(dist[i][i] < 0) {
            printf("Graph contains negative cycle!\n");
            return;
        }
    }
    
    // Print results
    printf("Shortest distances between all pairs:\n");
    printf("    ");
    for(int i = 0; i < n; i++) {
        printf("%4d ", i);
    }
    printf("\n");
    
    for(int i = 0; i < n; i++) {
        printf("%2d: ", i);
        for(int j = 0; j < n; j++) {
            if(dist[i][j] == INF) {
                printf(" INF ");
            } else {
                printf("%4d ", dist[i][j]);
            }
        }
        printf("\n");
    }
}

int main() {
    Graph g;
    int vertices, edges, u, v, weight;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    for(int i = 0; i < edges; i++) {
        printf("Edge %d (u v weight): ", i + 1);
        scanf("%d %d %d", &u, &v, &weight);
        addEdge(&g, u, v, weight);
    }
    
    floydWarshall(&g);
    
    return 0;
}

b) int findTheCity(int n, int** edges, int edgesSize, int* edgesColSize, int distanceThreshold) {
    // Initialize distance matrix
    int** dist = (int**)malloc(n * sizeof(int*));
    for(int i = 0; i < n; i++) {
        dist[i] = (int*)malloc(n * sizeof(int));
        for(int j = 0; j < n; j++) {
            dist[i][j] = (i == j) ? 0 : 10001;  // Large number
        }
    }
    
    // Set edges
    for(int i = 0; i < edgesSize; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        int w = edges[i][2];
        dist[u][v] = w;
        dist[v][u] = w;
    }
    
    // Floyd-Warshall
    for(int k = 0; k < n; k++) {
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < n; j++) {
                if(dist[i][k] + dist[k][j] < dist[i][j]) {
                    dist[i][j] = dist[i][k] + dist[k][j];
                }
            }
        }
    }
    
    // Count reachable cities within threshold
    int minCount = n;
    int bestCity = 0;
    
    for(int i = 0; i < n; i++) {
        int count = 0;
        for(int j = 0; j < n; j++) {
            if(i != j && dist[i][j] <= distanceThreshold) {
                count++;
            }
        }
        if(count <= minCount) {
            minCount = count;
            bestCity = i;
        }
    }
    
    // Cleanup
    for(int i = 0; i < n; i++) {
        free(dist[i]);
    }
    free(dist);
    
    return bestCity;
}

81)

a) #include <stdio.h>
#include <stdlib.h>
#include <limits.h>

#define MAX 100

typedef struct {
    int u, v, weight;
} Edge;

typedef struct {
    int vertices;
    int edges;
    Edge edgeList[MAX];
} Graph;

typedef struct {
    int parent[MAX];
    int rank[MAX];
} DisjointSet;

void initGraph(Graph* g, int vertices) {
    g->vertices = vertices;
    g->edges = 0;
}

void addEdge(Graph* g, int u, int v, int weight) {
    g->edgeList[g->edges].u = u;
    g->edgeList[g->edges].v = v;
    g->edgeList[g->edges].weight = weight;
    g->edges++;
}

int compareEdges(const void* a, const void* b) {
    return ((Edge*)a)->weight - ((Edge*)b)->weight;
}

void makeSet(DisjointSet* ds, int n) {
    for(int i = 0; i < n; i++) {
        ds->parent[i] = i;
        ds->rank[i] = 0;
    }
}

int find(DisjointSet* ds, int x) {
    if(ds->parent[x] != x) {
        ds->parent[x] = find(ds, ds->parent[x]);
    }
    return ds->parent[x];
}

void unionSets(DisjointSet* ds, int x, int y) {
    int rootX = find(ds, x);
    int rootY = find(ds, y);
    
    if(rootX != rootY) {
        if(ds->rank[rootX] < ds->rank[rootY]) {
            ds->parent[rootX] = rootY;
        } else if(ds->rank[rootX] > ds->rank[rootY]) {
            ds->parent[rootY] = rootX;
        } else {
            ds->parent[rootY] = rootX;
            ds->rank[rootX]++;
        }
    }
}

void kruskalMST(Graph* g) {
    // Sort edges by weight
    qsort(g->edgeList, g->edges, sizeof(Edge), compareEdges);
    
    DisjointSet ds;
    makeSet(&ds, g->vertices);
    
    Edge result[MAX];
    int resultSize = 0;
    int totalWeight = 0;
    
    for(int i = 0; i < g->edges; i++) {
        int u = g->edgeList[i].u;
        int v = g->edgeList[i].v;
        int weight = g->edgeList[i].weight;
        
        if(find(&ds, u) != find(&ds, v)) {
            unionSets(&ds, u, v);
            result[resultSize++] = g->edgeList[i];
            totalWeight += weight;
        }
    }
    
    printf("Minimum Spanning Tree Edges:\n");
    for(int i = 0; i < resultSize; i++) {
        printf("%d -- %d == %d\n", result[i].u, result[i].v, result[i].weight);
    }
    printf("Total weight: %d\n", totalWeight);
}

int main() {
    Graph g;
    int vertices, edges, u, v, weight;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    initGraph(&g, vertices);
    
    printf("Enter number of edges: ");
    scanf("%d", &edges);
    
    for(int i = 0; i < edges; i++) {
        printf("Edge %d (u v weight): ", i + 1);
        scanf("%d %d %d", &u, &v, &weight);
        addEdge(&g, u, v, weight);
    }
    
    kruskalMST(&g);
    
    return 0;
}

b) typedef struct {
    int u, v, dist;
} Edge;

int compareEdges(const void* a, const void* b) {
    return ((Edge*)a)->dist - ((Edge*)b)->dist;
}

int find(int* parent, int x) {
    if(parent[x] != x) {
        parent[x] = find(parent, parent[x]);
    }
    return parent[x];
}

void unionSet(int* parent, int* rank, int x, int y) {
    int rootX = find(parent, x);
    int rootY = find(parent, y);
    
    if(rootX != rootY) {
        if(rank[rootX] < rank[rootY]) {
            parent[rootX] = rootY;
        } else if(rank[rootX] > rank[rootY]) {
            parent[rootY] = rootX;
        } else {
            parent[rootY] = rootX;
            rank[rootX]++;
        }
    }
}

int minCostConnectPoints(int** points, int pointsSize, int* pointsColSize) {
    int n = pointsSize;
    int edgeCount = n * (n - 1) / 2;
    Edge* edges = (Edge*)malloc(edgeCount * sizeof(Edge));
    int idx = 0;
    
    // Calculate all pairwise distances
    for(int i = 0; i < n; i++) {
        for(int j = i + 1; j < n; j++) {
            edges[idx].u = i;
            edges[idx].v = j;
            edges[idx].dist = abs(points[i][0] - points[j][0]) + abs(points[i][1] - points[j][1]);
            idx++;
        }
    }
    
    qsort(edges, edgeCount, sizeof(Edge), compareEdges);
    
    int* parent = (int*)malloc(n * sizeof(int));
    int* rank = (int*)calloc(n, sizeof(int));
    for(int i = 0; i < n; i++) {
        parent[i] = i;
    }
    
    int totalCost = 0;
    int edgesUsed = 0;
    
    for(int i = 0; i < edgeCount && edgesUsed < n - 1; i++) {
        int u = edges[i].u;
        int v = edges[i].v;
        int dist = edges[i].dist;
        
        if(find(parent, u) != find(parent, v)) {
            unionSet(parent, rank, u, v);
            totalCost += dist;
            edgesUsed++;
        }
    }
    
    free(edges);
    free(parent);
    free(rank);
    
    return totalCost;
}

82)

a) #include <stdio.h>

// Lower bound: first index where arr[i] >= target
int lowerBound(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    int result = n;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] >= target) {
            result = mid;
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }
    
    return result;
}

// Upper bound: first index where arr[i] > target
int upperBound(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    int result = n;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(arr[mid] > target) {
            result = mid;
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }
    
    return result;
}

// Count occurrences of target
int countOccurrences(int arr[], int n, int target) {
    int lb = lowerBound(arr, n, target);
    int ub = upperBound(arr, n, target);
    return ub - lb;
}

int main() {
    int arr[] = {1, 2, 2, 2, 3, 4, 5, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);
    int target;
    
    printf("Array: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    printf("Enter target: ");
    scanf("%d", &target);
    
    int lb = lowerBound(arr, n, target);
    int ub = upperBound(arr, n, target);
    int count = countOccurrences(arr, n, target);
    
    printf("Lower bound index: %d (arr[%d] = %d)\n", lb, lb, lb < n ? arr[lb] : -1);
    printf("Upper bound index: %d (arr[%d] = %d)\n", ub, ub, ub < n ? arr[ub] : -1);
    printf("Count of %d: %d\n", target, count);
    
    return 0;
}

b) int searchInsert(int* nums, int numsSize, int target) {
    int left = 0, right = numsSize - 1;
    
    while(left <= right) {
        int mid = left + (right - left) / 2;
        
        if(nums[mid] == target) {
            return mid;
        } else if(nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return left;
}

83)

a) #include <stdio.h>

void selectionSort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        int minIndex = i;
        
        for(int j = i + 1; j < n; j++) {
            if(arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        
        if(minIndex != i) {
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        }
        
        // Print after each pass
        printf("Pass %d: ", i + 1);
        for(int k = 0; k < n; k++) {
            printf("%d ", arr[k]);
        }
        printf("\n");
    }
}

// Stable selection sort
void stableSelectionSort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        int minIndex = i;
        
        for(int j = i + 1; j < n; j++) {
            if(arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        
        // Shift elements instead of swapping to maintain stability
        int minValue = arr[minIndex];
        for(int k = minIndex; k > i; k--) {
            arr[k] = arr[k - 1];
        }
        arr[i] = minValue;
        
        printf("Stable Pass %d: ", i + 1);
        for(int k = 0; k < n; k++) {
            printf("%d ", arr[k]);
        }
        printf("\n");
    }
}

int main() {
    int arr[100], n, choice;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("\nChoose sort type:\n");
    printf("1. Standard Selection Sort\n");
    printf("2. Stable Selection Sort\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    if(choice == 1) {
        selectionSort(arr, n);
    } else {
        stableSelectionSort(arr, n);
    }
    
    printf("\nSorted array: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
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

84)

a)#include <stdio.h>

void insertionSort(int arr[], int n) {
    for(int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        
        while(j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
        
        printf("Pass %d: ", i);
        for(int k = 0; k < n; k++) {
            printf("%d ", arr[k]);
        }
        printf("\n");
    }
}

// Binary insertion sort (use binary search to find insertion position)
int binarySearchForInsertion(int arr[], int val, int low, int high) {
    while(low <= high) {
        int mid = low + (high - low) / 2;
        
        if(arr[mid] == val) {
            return mid;
        } else if(arr[mid] < val) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return low;
}

void binaryInsertionSort(int arr[], int n) {
    for(int i = 1; i < n; i++) {
        int key = arr[i];
        int pos = binarySearchForInsertion(arr, key, 0, i - 1);
        
        // Shift elements
        for(int j = i - 1; j >= pos; j--) {
            arr[j + 1] = arr[j];
        }
        arr[pos] = key;
        
        printf("Binary Pass %d: ", i);
        for(int k = 0; k < n; k++) {
            printf("%d ", arr[k]);
        }
        printf("\n");
    }
}

int main() {
    int arr[100], n, choice;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    printf("Enter %d elements: ", n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    
    printf("\nChoose sort type:\n");
    printf("1. Standard Insertion Sort\n");
    printf("2. Binary Insertion Sort\n");
    printf("Enter choice: ");
    scanf("%d", &choice);
    
    if(choice == 1) {
        insertionSort(arr, n);
    } else {
        binaryInsertionSort(arr, n);
    }
    
    printf("\nSorted array: ");
    for(int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}

b) int findPeakElement(int* nums, int numsSize) {
    int left = 0, right = numsSize - 1;
    
    while(left < right) {
        int mid = left + (right - left) / 2;
        
        if(nums[mid] > nums[mid + 1]) {
            // Peak is on left side (including mid)
            right = mid;
        } else {
            // Peak is on right side
            left = mid + 1;
        }
    }
    
    return left;
}


 

