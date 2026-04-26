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


