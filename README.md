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

#include <stdio.h>

int main() {
    int nums[] = {1, 2, 3, 4};
    int n = 4;
    int result[4];
    int i;

    result[0] = 1;
    for(i = 1; i < n; i++) {
        result[i] = result[i - 1] * nums[i - 1];
    }

    int right = 1;
    for(i = n - 1; i >= 0; i--) {
        result[i] = result[i] * right;
        right = right * nums[i];
    }

    printf("Product of Array Except Self:\n");
    for(i = 0; i < n; i++) {
        printf("%d ", result[i]);
    }

    return 0;
}

Day 20

#include <stdio.h>

int main() {
    int arr[] = {1, -2, 3, -2};
    int n = 4;
    int i;

    int total = arr[0];
    int maxSum = arr[0], curMax = arr[0];
    int minSum = arr[0], curMin = arr[0];

    for(i = 1; i < n; i++) {
        if(curMax + arr[i] > arr[i])
            curMax = curMax + arr[i];
        else
            curMax = arr[i];

        if(curMax > maxSum)
            maxSum = curMax;

        if(curMin + arr[i] < arr[i])
            curMin = curMin + arr[i];
        else
            curMin = arr[i];

        if(curMin < minSum)
            minSum = curMin;

        total += arr[i];
    }

    if(maxSum < 0)
        printf("Maximum Circular Subarray Sum = %d", maxSum);
    else {
        int circularSum = total - minSum;
        if(circularSum > maxSum)
            printf("Maximum Circular Subarray Sum = %d", circularSum);
        else
            printf("Maximum Circular Subarray Sum = %d", maxSum);
    }

    return 0;
}

Day 21

#include <stdio.h>

int main() {
    int arr[] = {-1, 0, 1, 2, -1, -4};
    int n = 6;
    int i, j, k;

    printf("Triplets with sum 0:\n");

    for(i = 0; i < n - 2; i++) {
        for(j = i + 1; j < n - 1; j++) {
            for(k = j + 1; k < n; k++) {
                if(arr[i] + arr[j] + arr[k] == 0) {
                    printf("%d %d %d\n", arr[i], arr[j], arr[k]);
                }
            }
        }
    }

    return 0;
}

Day 22

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int main() {
    struct Node *head = NULL, *temp, *newNode;
    int i;

    for(i = 1; i <= 5; i++) {
        newNode = (struct Node*)malloc(sizeof(struct Node));
        newNode->data = i;
        newNode->next = NULL;

        if(head == NULL) {
            head = newNode;
            temp = head;
        } else {
            temp->next = newNode;
            temp = newNode;
        }
    }

    struct Node *slow = head, *fast = head;

    while(fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
    }

    printf("Middle Element = %d", slow->data);

    return 0;
}

Day 23

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int main() {

Day 24

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int main() {

Day 25

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int main() {
    struct Node *head, *second, *third, *fourth;

    head = (struct Node*)malloc(sizeof(struct Node));
    second = (struct Node*)malloc(sizeof(struct Node));
    third = (struct Node*)malloc(sizeof(struct Node));
    fourth = (struct Node*)malloc(sizeof(struct Node));

    head->data = 1; head->next = second;
    second->data = 2; second->next = third;
    third->data = 3; third->next = fourth;
    fourth->data = 4; fourth->next = second;   // Creates cycle

    struct Node *slow = head, *fast = head;
    int cycle = 0;

    while(fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;

        if(slow == fast) {
            cycle = 1;
            break;
        }
    }

    if(cycle)
        printf("Cycle Detected");
    else
        printf("No Cycle");

    return 0;
}

Day 26

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int main() {
    struct Node *head = NULL, *temp, *newNode;
    int i, key = 6;

    int values[] = {1, 2, 6, 3, 4, 5, 6};

    for(i = 0; i < 7; i++) {
        newNode = (struct Node*)malloc(sizeof(struct Node));
        newNode->data = values[i];
        newNode->next = NULL;

        if(head == NULL) {
            head = newNode;
            temp = head;
        } else {
            temp->next = newNode;
            temp = newNode;
        }
    }

    while(head != NULL && head->data == key) {
        head = head->next;
    }

    temp = head;

    while(temp != NULL && temp->next != NULL) {
        if(temp->next->data == key)
            temp->next = temp->next->next;
        else
            temp = temp->next;
    }

    printf("Linked List after removal:\n");

    temp = head;
    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }

    return 0;
}

Day 27

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int main() {
    struct Node *head, *second, *third, *fourth;

    head = (struct Node*)malloc(sizeof(struct Node));
    second = (struct Node*)malloc(sizeof(struct Node));
    third = (struct Node*)malloc(sizeof(struct Node));
    fourth = (struct Node*)malloc(sizeof(struct Node));

    head->data = 1; head->next = second;
    second->data = 2; second->next = third;
    third->data = 3; third->next = fourth;
    fourth->data = 4; fourth->next = second;   // Cycle starts at node 2

    struct Node *slow = head, *fast = head;
    int cycle = 0;

    while(fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;

        if(slow == fast) {
            cycle = 1;
            break;
        }
    }

    if(cycle) {
        slow = head;

        while(slow != fast) {
            slow = slow->next;
            fast = fast->next;
        }

        printf("Cycle starts at node with value = %d", slow->data);
    } else {
        printf("No Cycle");
    }

    return 0;
}

Day 28

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* head = NULL;

void addAtHead(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = head;
    head = newNode;
}

void addAtTail(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    struct Node* temp = head;

    newNode->data = val;
    newNode->next = NULL;

    if(head == NULL) {
        head = newNode;
        return;
    }

    while(temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
}

void printList() {
    struct Node* temp = head;

    while(temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
}

int main() {
    addAtHead(10);
    addAtHead(20);
    addAtTail(30);
    addAtTail(40);

    printf("Linked List:\n");
    printList();

    return 0;
}

Day 29

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

int main() {
    struct Node *head, *second, *third, *fourth;
    struct Node *slow, *fast, *prev;

    head = (struct Node*)malloc(sizeof(struct Node));
    second = (struct Node*)malloc(sizeof(struct Node));
    third = (struct Node*)malloc(sizeof(struct Node));
    fourth = (struct Node*)malloc(sizeof(struct Node));

    head->data = 1;   head->next = second;
    second->data = 2; second->next = third;
    third->data = 3;  third->next = fourth;
    fourth->data = 4; fourth->next = second;   // Cycle created

    slow = head;
    fast = head;

    while(fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;

        if(slow == fast)
            break;
    }

    if(slow == fast) {
        slow = head;

        while(slow != fast) {
            prev = fast;
            slow = slow->next;
            fast = fast->next;
        }

        prev->next = NULL;   // Remove cycle
    }

    printf("Cycle removed. Linked List:\n");

    while(head != NULL) {
        printf("%d ", head->data);
        head = head->next;
    }

    return 0;
}

Day 30

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

int main() {
    struct Node *head = NULL, *temp, *newNode;
    struct Node *slow, *fast, *prev = NULL, *curr, *nextNode;
    int values[] = {1, 2, 2, 1};
    int i, flag = 1;

    for(i = 0; i < 4; i++) {
        newNode = (struct Node*)malloc(sizeof(struct Node));
        newNode->data = values[i];
        newNode->next = NULL;

        if(head == NULL) {
            head = newNode;
            temp = head;
        } else {
            temp->next = newNode;
            temp = newNode;
        }
    }

    slow = head;
    fast = head;

    while(fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
    }

    curr = slow;
    while(curr != NULL) {
        nextNode = curr->next;
        curr->next = prev;
        prev = curr;
        curr = nextNode;
    }

    temp = head;
    while(prev != NULL) {
        if(temp->data != prev->data) {
            flag = 0;
            break;
        }
        temp = temp->next;
        prev = prev->next;
    }

    if(flag)
        printf("Palindrome Linked List");
    else
        printf("Not Palindrome Linked List");

    return 0;
}

Day 31

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

struct Node* createNode(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = NULL;
    return newNode;
}

void printList(struct Node* head) {
    while(head != NULL) {
        printf("%d ", head->data);
        head = head->next;
    }
}

int main() {
    struct Node *l1, *l2, *result, *temp, *tail;
    int carry = 0, sum;

    l1 = createNode(2);
    l1->next = createNode(4);
    l1->next->next = createNode(3);

    l2 = createNode(5);
    l2->next = createNode(6);
    l2->next->next = createNode(4);

    result = NULL;
    tail = NULL;

    while(l1 != NULL || l2 != NULL || carry) {
        sum = carry;

        if(l1 != NULL) {
            sum += l1->data;
            l1 = l1->next;
        }

        if(l2 != NULL) {
            sum += l2->data;
            l2 = l2->next;
        }

        temp = createNode(sum % 10);
        carry = sum / 10;

        if(result == NULL) {
            result = temp;
            tail = temp;
        } else {
            tail->next = temp;
            tail = temp;
        }
    }

    printf("Sum List:\n");
    printList(result);

    return 0;
}

Day 32

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

struct Node* createNode(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->next = NULL;
    return newNode;
}

struct Node* reverse(struct Node* head) {
    struct Node *prev = NULL, *nextNode;

    while(head != NULL) {
        nextNode = head->next;
        head->next = prev;
        prev = head;
        head = nextNode;
    }
    return prev;
}

void printList(struct Node* head) {
    while(head != NULL) {
        printf("%d ", head->data);
        head = head->next;
    }
}

int main() {
    struct Node *l1, *l2, *result = NULL, *temp, *tail = NULL;
    int carry = 0, sum;

    l1 = createNode(7);
    l1->next = createNode(2);
    l1->next->next = createNode(4);
    l1->next->next->next = createNode(3);

    l2 = createNode(5);
    l2->next = createNode(6);
    l2->next->next = createNode(4);

    l1 = reverse(l1);
    l2 = reverse(l2);

    while(l1 != NULL || l2 != NULL || carry) {
        sum = carry;

        if(l1 != NULL) {
            sum += l1->data;
            l1 = l1->next;
        }

        if(l2 != NULL) {
            sum += l2->data;
            l2 = l2->next;
        }

        temp = createNode(sum % 10);
        carry = sum / 10;

        temp->next = result;
        result = temp;
    }

    printf("Sum List:\n");
    printList(result);

    return 0;
}


Day 33

#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    char stack[100];
    int top = -1, i;
    int valid = 1;

    printf("Enter parentheses string: ");
    scanf("%s", str);

    for(i = 0; i < strlen(str); i++) {
        if(str[i] == '(' || str[i] == '{' || str[i] == '[') {
            stack[++top] = str[i];
        }
        else {
            if(top == -1) {
                valid = 0;
                break;
            }

            if((str[i] == ')' && stack[top] == '(') ||
               (str[i] == '}' && stack[top] == '{') ||
               (str[i] == ']' && stack[top] == '[')) {
                top--;
            }
            else {
                valid = 0;
                break;
            }
        }
    }

    if(top != -1)
        valid = 0;

    if(valid)
        printf("Valid Parentheses");
    else
        printf("Invalid Parentheses");

    return 0;
}

Day 34

#include <stdio.h>

#define MAX 100

int stack[MAX];
int minStack[MAX];
int top = -1;
int minTop = -1;

void push(int val) {
    stack[++top] = val;

    if(minTop == -1 || val <= minStack[minTop]) {
        minStack[++minTop] = val;
    }
}

void pop() {
    if(top == -1) {
        printf("Stack is empty\n");
        return;
    }

    if(stack[top] == minStack[minTop]) {
        minTop--;
    }

    top--;
}

int topElement() {
    if(top == -1)
        return -1;
    return stack[top];
}

int getMin() {
    if(minTop == -1)
        return -1;
    return minStack[minTop];
}

int main() {
    push(5);
    push(3);
    push(7);
    push(2);

    printf("Top Element = %d\n", topElement());
    printf("Minimum Element = %d\n", getMin());

    pop();
    printf("After Pop, Minimum Element = %d\n", getMin());

    return 0;
}

Day 35

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX 100

int stack[MAX];
int top = -1;

void push(int val) {
    stack[++top] = val;
}

int pop() {
    return stack[top--];
}

int main() {
    char *tokens[] = {"2", "1", "+", "3", "*"};
    int n = 5;
    int i, a, b;

    for(i = 0; i < n; i++) {
        if(strcmp(tokens[i], "+") == 0) {
            b = pop();
            a = pop();
            push(a + b);
        }
        else if(strcmp(tokens[i], "-") == 0) {
            b = pop();
            a = pop();
            push(a - b);
        }
        else if(strcmp(tokens[i], "*") == 0) {
            b = pop();
            a = pop();
            push(a * b);
        }
        else if(strcmp(tokens[i], "/") == 0) {
            b = pop();
            a = pop();
            push(a / b);
        }
        else {
            push(atoi(tokens[i]));
        }
    }

    printf("Result = %d", pop());

    return 0;
}

Day 36

#include <stdio.h>
#include <ctype.h>
#include <string.h>

int main() {
    char s[] = "3+2*2";
    int num = 0, result = 0, lastNum = 0;
    char op = '+';
    int i;

    for(i = 0; i <= strlen(s); i++) {
        if(isdigit(s[i])) {
            num = num * 10 + (s[i] - '0');
        }

        if((!isdigit(s[i]) && s[i] != ' ') || s[i] == '\0') {

            if(op == '+') {
                result += lastNum;
                lastNum = num;
            }
            else if(op == '-') {
                result += lastNum;
                lastNum = -num;
            }
            else if(op == '*') {
                lastNum = lastNum * num;
            }
            else if(op == '/') {
                lastNum = lastNum / num;
            }

            op = s[i];
            num = 0;
        }
    }

    result += lastNum;

    printf("Result = %d", result);

    return 0;
}

Day 37

#include <stdio.h>

#define MAX 100

int stack1[MAX], stack2[MAX];
int top1 = -1, top2 = -1;

void push1(int x) {
    stack1[++top1] = x;
}

int pop1() {
    return stack1[top1--];
}

void push2(int x) {
    stack2[++top2] = x;
}

int pop2() {
    return stack2[top2--];
}

void enqueue(int x) {
    push1(x);
}

int dequeue() {
    if(top2 == -1) {
        while(top1 != -1) {
            push2(pop1());
        }
    }

    if(top2 == -1) {
        printf("Queue is empty\n");
        return -1;
    }

    return pop2();
}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);

    printf("Dequeued = %d\n", dequeue());
    printf("Dequeued = %d\n", dequeue());

    enqueue(40);

    printf("Dequeued = %d\n", dequeue());

    return 0;
}

Day 38

#include <stdio.h>

#define SIZE 5

int deque[SIZE];
int front = -1, rear = -1;

int isFull() {
    return (front == 0 && rear == SIZE - 1) || (front == rear + 1);
}

int isEmpty() {
    return front == -1;
}

void insertFront(int val) {
    if(isFull()) {
        printf("Deque is Full\n");
        return;
    }

    if(front == -1) {
        front = rear = 0;
    }
    else if(front == 0) {
        front = SIZE - 1;
    }
    else {
        front--;
    }

    deque[front] = val;
}

void insertRear(int val) {
    if(isFull()) {
        printf("Deque is Full\n");
        return;
    }

    if(front == -1) {
        front = rear = 0;
    }
    else if(rear == SIZE - 1) {
        rear = 0;
    }
    else {
        rear++;
    }

    deque[rear] = val;
}

int deleteFront() {
    int val;

    if(isEmpty()) {
        printf("Deque is Empty\n");
        return -1;
    }

    val = deque[front];

    if(front == rear) {
        front = rear = -1;
    }
    else if(front == SIZE - 1) {
        front = 0;
    }
    else {
        front++;
    }

    return val;
}

int deleteRear() {
    int val;

    if(isEmpty()) {
        printf("Deque is Empty\n");
        return -1;
    }

    val = deque[rear];

    if(front == rear) {
        front = rear = -1;
    }
    else if(rear == 0) {
        rear = SIZE - 1;
    }
    else {
        rear--;
    }

    return val;
}

int main() {
    insertRear(10);
    insertRear(20);
    insertFront(5);
    insertFront(2);

    printf("Delete Front = %d\n", deleteFront());
    printf("Delete Rear = %d\n", deleteRear());

    insertRear(30);
    insertRear(40);

    printf("Delete Front = %d\n", deleteFront());

    return 0;
}

Day 39

#include <stdio.h>

#define SIZE 100

int arr[SIZE];
int n = 0;
int k = 3;

void sort() {
    int i, j, temp;

    for(i = 0; i < n - 1; i++) {
        for(j = i + 1; j < n; j++) {
            if(arr[i] < arr[j]) {
                temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
}

void add(int val) {
    arr[n++] = val;
    sort();

    if(n >= k)
        printf("Kth Largest = %d\n", arr[k - 1]);
    else
        printf("Not enough elements\n");
}

int main() {
    add(4);
    add(5);
    add(8);
    add(2);
    add(3);
    add(10);

    return 0;
}

Day 40

#include <stdio.h>

int main() {
    int nums[] = {1, 3, -1, -3, 5, 3, 6, 7};
    int n = 8;
    int k = 3;
    int i, j, max;

    printf("Sliding Window Maximum:\n");

    for(i = 0; i <= n - k; i++) {
        max = nums[i];

        for(j = i; j < i + k; j++) {
            if(nums[j] > max) {
                max = nums[j];
            }
        }

        printf("%d ", max);
    }

    return 0;
}

Day 41

#include <stdio.h>

int main() {
    int nums[] = {1, 1, 1, 2, 2, 3};
    int n = 6, k = 2;
    int freq[100] = {0};
    int i, j, maxIndex;

    for(i = 0; i < n; i++) {
        freq[nums[i]]++;
    }

    printf("Top %d Frequent Elements:\n", k);

    for(i = 0; i < k; i++) {
        maxIndex = 0;

        for(j = 1; j < 100; j++) {
            if(freq[j] > freq[maxIndex]) {
                maxIndex = j;
            }
        }

        printf("%d ", maxIndex);
        freq[maxIndex] = 0;
    }

    return 0;
}

Day 42

#include <stdio.h>

int main() {
    int temp[] = {73, 74, 75, 71, 69, 72, 76, 73};
    int n = 8;
    int result[8] = {0};
    int stack[8];
    int top = -1;
    int i;

    for(i = 0; i < n; i++) {
        while(top != -1 && temp[i] > temp[stack[top]]) {
            int index = stack[top--];
            result[index] = i - index;
        }

        stack[++top] = i;
    }

    printf("Days to wait for warmer temperature:\n");

    for(i = 0; i < n; i++) {
        printf("%d ", result[i]);
    }

    return 0;
}

Day 43

#include <stdio.h>

int main() {
    char tasks[] = {'A', 'A', 'A', 'B', 'B', 'B'};
    int n = 6;
    int cool = 2;

    int freq[26] = {0};
    int i, maxFreq = 0, maxCount = 0;
    int result;

    for(i = 0; i < n; i++) {
        freq[tasks[i] - 'A']++;
    }

    for(i = 0; i < 26; i++) {
        if(freq[i] > maxFreq) {
            maxFreq = freq[i];
        }
    }

    for(i = 0; i < 26; i++) {
        if(freq[i] == maxFreq) {
            maxCount++;
        }
    }

    result = (maxFreq - 1) * (cool + 1) + maxCount;

    if(result < n)
        result = n;

    printf("Minimum intervals needed = %d", result);

    return 0;
}

Day 44

#include <stdio.h>

int arr[100];
int n = 0;

void sort() {
    int i, j, temp;

    for(i = 0; i < n - 1; i++) {
        for(j = i + 1; j < n; j++) {
            if(arr[i] > arr[j]) {
                temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
}

void addNum(int num) {
    arr[n++] = num;
    sort();
}

double findMedian() {
    if(n % 2 == 0)
        return (arr[n/2 - 1] + arr[n/2]) / 2.0;
    else
        return arr[n/2];
}

int main() {
    addNum(1);
    addNum(2);
    printf("Median = %.1f\n", findMedian());

    addNum(3);
    printf("Median = %.1f\n", findMedian());

    return 0;
}

Day 45

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *left, *right;
};

struct Node* createNode(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = createNode(1);
    root->right = createNode(2);
    root->right->left = createNode(3);

    printf("Inorder Traversal:\n");
    inorder(root);

    return 0;
}

Day 46

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *left, *right;
};

struct Node* createNode(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = val;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

void preorder(struct Node* root) {
    if(root != NULL) {
        printf("%d ", root->data);
        preorder(root->left);
        preorder(root->right);
    }
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);

    printf("Preorder Traversal:\n");
    preorder(root);

    return 0;
}

Day 47








