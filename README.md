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

Day 15

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

Day 16

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

Day 17

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

Day 18

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

Day 19

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

Day 20

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

Day 21

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

Day 22

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

int main() {

Day 23

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

Day 24

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

Day 26

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

Day 27

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

Day 28

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

Day 29

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

Day 30

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

Day 30#include <stdio.h>
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

Day 31

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

Day 32

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

Day 33

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

Day 34

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

Day 35

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

Day 36

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

Day 37

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

Day 38#include <stdio.h>

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

Day 39

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

Day 40

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

Day 41

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

Day 42

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

Day 43

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

Day 44

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

int maxDepth(struct Node* root) {
    if(root == NULL)
        return 0;

    int leftDepth = maxDepth(root->left);
    int rightDepth = maxDepth(root->right);

    if(leftDepth > rightDepth)
        return leftDepth + 1;
    else
        return rightDepth + 1;
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);

    printf("Maximum Depth = %d", maxDepth(root));

    return 0;
}

Day 46

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

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

void levelOrder(struct Node* root) {
    if(root == NULL) return;

    struct Node* queue[MAX];
    int front = 0, rear = 0;

    queue[rear++] = root;

    while(front < rear) {
        struct Node* curr = queue[front++];

        printf("%d ", curr->data);

        if(curr->left != NULL)
            queue[rear++] = curr->left;

        if(curr->right != NULL)
            queue[rear++] = curr->right;
    }
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);

    printf("Level Order Traversal:\n");
    levelOrder(root);

    return 0;
}

Day 47

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

int maxDepth(struct Node* root) {
    if(root == NULL)
        return 0;

    int leftDepth = maxDepth(root->left);
    int rightDepth = maxDepth(root->right);

    return (leftDepth > rightDepth ? leftDepth : rightDepth) + 1;
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);
    root->left->left->left = createNode(6);

    printf("Maximum Depth = %d\n", maxDepth(root));

    return 0;
}

Day 48

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

int sumOfLeftLeaves(struct Node* root) {
    if(root == NULL)
        return 0;

    int sum = 0;

    if(root->left != NULL) {
        if(root->left->left == NULL && root->left->right == NULL)
            sum += root->left->data;
        else
            sum += sumOfLeftLeaves(root->left);
    }

    sum += sumOfLeftLeaves(root->right);

    return sum;
}

int main() {
    struct Node* root = createNode(3);
    root->left = createNode(9);
    root->right = createNode(20);
    root->right->left = createNode(15);
    root->right->right = createNode(7);

    printf("Sum of Left Leaves = %d\n", sumOfLeftLeaves(root));

    return 0;
}

Day 49

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

struct Node* insertBST(struct Node* root, int val) {
    if(root == NULL)
        return createNode(val);

    if(val < root->data)
        root->left = insertBST(root->left, val);
    else
        root->right = insertBST(root->right, val);

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

    root = insertBST(root, 5);
    insertBST(root, 3);
    insertBST(root, 7);
    insertBST(root, 2);
    insertBST(root, 4);
    insertBST(root, 6);
    insertBST(root, 8);

    printf("BST Inorder Traversal:\n");
    inorder(root);

    return 0;
}

Day 50

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

struct Node* insertBST(struct Node* root, int val) {
    if(root == NULL)
        return createNode(val);

    if(val < root->data)
        root->left = insertBST(root->left, val);
    else
        root->right = insertBST(root->right, val);

    return root;
}

int searchBST(struct Node* root, int key) {
    if(root == NULL)
        return 0;

    if(root->data == key)
        return 1;

    if(key < root->data)
        return searchBST(root->left, key);
    else
        return searchBST(root->right, key);
}

int main() {
    struct Node* root = NULL;

    int arr[] = {8, 3, 10, 1, 6, 14, 4, 7, 13};
    int n = 9, i;

    for(i = 0; i < n; i++) {
        root = insertBST(root, arr[i]);
    }

    int key = 7;

    if(searchBST(root, key))
        printf("%d found in BST\n", key);
    else
        printf("%d not found in BST\n", key);

    return 0;
}

Day 51

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

struct Node* insertBST(struct Node* root, int val) {
    if(root == NULL)
        return createNode(val);

    if(val < root->data)
        root->left = insertBST(root->left, val);
    else
        root->right = insertBST(root->right, val);

    return root;
}

struct Node* LCA(struct Node* root, int p, int q) {
    if(root == NULL)
        return NULL;

    if(p < root->data && q < root->data)
        return LCA(root->left, p, q);

    if(p > root->data && q > root->data)
        return LCA(root->right, p, q);

    return root;
}

int main() {
    struct Node* root = NULL;

    int arr[] = {6, 2, 8, 0, 4, 7, 9, 3, 5};
    int n = 9, i;

    for(i = 0; i < n; i++) {
        root = insertBST(root, arr[i]);
    }

    int p = 2, q = 8;

    struct Node* lca = LCA(root, p, q);

    if(lca != NULL)
        printf("LCA of %d and %d = %d\n", p, q, lca->data);

    return 0;
}

Day 52

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

struct Node* LCA(struct Node* root, struct Node* p, struct Node* q) {
    if(root == NULL)
        return NULL;

    if(root == p || root == q)
        return root;

    struct Node* left = LCA(root->left, p, q);
    struct Node* right = LCA(root->right, p, q);

    if(left != NULL && right != NULL)
        return root;

    if(left != NULL)
        return left;
    else
        return right;
}

int main() {
    struct Node* root = createNode(3);
    root->left = createNode(5);
    root->right = createNode(1);
    root->left->left = createNode(6);
    root->left->right = createNode(2);
    root->right->left = createNode(0);
    root->right->right = createNode(8);

    struct Node* p = root->left;          // 5
    struct Node* q = root->right;         // 1

    struct Node* lca = LCA(root, p, q);

    if(lca != NULL)
        printf("LCA = %d\n", lca->data);

    return 0;
}

Day 53

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

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

void levelOrder(struct Node* root) {
    if(root == NULL) return;

    struct Node* queue[MAX];
    int front = 0, rear = 0;

    queue[rear++] = root;

    while(front < rear) {
        struct Node* curr = queue[front++];
        printf("%d ", curr->data);

        if(curr->left)
            queue[rear++] = curr->left;

        if(curr->right)
            queue[rear++] = curr->right;
    }
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);
    root->right->left = createNode(6);
    root->right->right = createNode(7);

    printf("Level Order Traversal:\n");
    levelOrder(root);

    return 0;
}

Day 54

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

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

void zigzagLevelOrder(struct Node* root) {
    if(root == NULL) return;

    struct Node* queue[MAX];
    int front = 0, rear = 0;
    int level = 0;

    queue[rear++] = root;

    while(front < rear) {
        int size = rear - front;
        int arr[MAX];

        for(int i = 0; i < size; i++) {
            struct Node* curr = queue[front++];
            arr[i] = curr->data;

            if(curr->left)
                queue[rear++] = curr->left;

            if(curr->right)
                queue[rear++] = curr->right;
        }

        if(level % 2 == 0) {
            for(int i = 0; i < size; i++)
                printf("%d ", arr[i]);
        } else {
            for(int i = size - 1; i >= 0; i--)
                printf("%d ", arr[i]);
        }

        level++;
    }
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);
    root->right->left = createNode(6);
    root->right->right = createNode(7);

    printf("Zigzag Level Order Traversal:\n");
    zigzagLevelOrder(root);

    return 0;
}

Day 55

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

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

void rightSideView(struct Node* root) {
    if(root == NULL) return;

    struct Node* queue[MAX];
    int front = 0, rear = 0;

    queue[rear++] = root;

    while(front < rear) {
        int size = rear - front;

        for(int i = 0; i < size; i++) {
            struct Node* curr = queue[front++];

            // last node of this level
            if(i == size - 1)
                printf("%d ", curr->data);

            if(curr->left)
                queue[rear++] = curr->left;

            if(curr->right)
                queue[rear++] = curr->right;
        }
    }
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->right = createNode(5);
    root->right->right = createNode(4);

    printf("Right Side View:\n");
    rightSideView(root);

    return 0;
}

Day 56

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

int isMirror(struct Node* t1, struct Node* t2) {
    if(t1 == NULL && t2 == NULL)
        return 1;

    if(t1 == NULL || t2 == NULL)
        return 0;

    return (t1->data == t2->data) &&
           isMirror(t1->left, t2->right) &&
           isMirror(t1->right, t2->left);
}

int isSymmetric(struct Node* root) {
    if(root == NULL)
        return 1;

    return isMirror(root->left, root->right);
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(2);
    root->left->left = createNode(3);
    root->left->right = createNode(4);
    root->right->left = createNode(4);
    root->right->right = createNode(3);

    if(isSymmetric(root))
        printf("Tree is Symmetric");
    else
        printf("Tree is Not Symmetric");

    return 0;
}

Day 57

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

void flatten(struct Node* root) {
    if(root == NULL)
        return;

    flatten(root->left);
    flatten(root->right);

    if(root->left != NULL) {
        struct Node* temp = root->right;
        root->right = root->left;
        root->left = NULL;

        struct Node* t = root->right;
        while(t->right != NULL)
            t = t->right;

        t->right = temp;
    }
}

void printList(struct Node* root) {
    while(root != NULL) {
        printf("%d ", root->data);
        root = root->right;
    }
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(5);
    root->left->left = createNode(3);
    root->left->right = createNode(4);
    root->right->right = createNode(6);

    flatten(root);

    printf("Flattened Tree:\n");
    printList(root);

    return 0;
}

Day 58

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

int search(int inorder[], int start, int end, int value) {
    for(int i = start; i <= end; i++) {
        if(inorder[i] == value)
            return i;
    }
    return -1;
}

struct Node* buildTree(int preorder[], int inorder[], int start, int end, int *preIndex) {
    if(start > end)
        return NULL;

    struct Node* root = createNode(preorder[*preIndex]);
    (*preIndex)++;

    if(start == end)
        return root;

    int inIndex = search(inorder, start, end, root->data);

    root->left = buildTree(preorder, inorder, start, inIndex - 1, preIndex);
    root->right = buildTree(preorder, inorder, inIndex + 1, end, preIndex);

    return root;
}

void inorderPrint(struct Node* root) {
    if(root != NULL) {
        inorderPrint(root->left);
        printf("%d ", root->data);
        inorderPrint(root->right);
    }
}

int main() {
    int preorder[] = {3, 9, 20, 15, 7};
    int inorder[] = {9, 3, 15, 20, 7};
    int n = 5;

    int preIndex = 0;

    struct Node* root = buildTree(preorder, inorder, 0, n - 1, &preIndex);

    printf("Inorder of constructed tree:\n");
    inorderPrint(root);

    return 0;
}

Day 59

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

int search(int inorder[], int start, int end, int value) {
    for(int i = start; i <= end; i++) {
        if(inorder[i] == value)
            return i;
    }
    return -1;
}

struct Node* buildTree(int inorder[], int postorder[], int start, int end, int *postIndex) {
    if(start > end)
        return NULL;

    struct Node* root = createNode(postorder[*postIndex]);
    (*postIndex)--;

    if(start == end)
        return root;

    int inIndex = search(inorder, start, end, root->data);

    root->right = buildTree(inorder, postorder, inIndex + 1, end, postIndex);
    root->left  = buildTree(inorder, postorder, start, inIndex - 1, postIndex);

    return root;
}

void preorderPrint(struct Node* root) {
    if(root != NULL) {
        printf("%d ", root->data);
        preorderPrint(root->left);
        preorderPrint(root->right);
    }
}

int main() {
    int inorder[] = {9, 3, 15, 20, 7};
    int postorder[] = {9, 15, 7, 20, 3};
    int n = 5;

    int postIndex = n - 1;

    struct Node* root = buildTree(inorder, postorder, 0, n - 1, &postIndex);

    printf("Preorder of constructed tree:\n");
    preorderPrint(root);

    return 0;
}

Day 60

#include <stdio.h>
#include <stdlib.h>

#define MINCOVERED 0
#define COVERED 1
#define CAMERA 2

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

int cameras = 0;

int dfs(struct Node* root) {
    if(root == NULL)
        return COVERED;

    int left = dfs(root->left);
    int right = dfs(root->right);

    if(left == MINCOVERED || right == MINCOVERED) {
        cameras++;
        return CAMERA;
    }

    if(left == CAMERA || right == CAMERA)
        return COVERED;

    return MINCOVERED;
}

int minCameraCover(struct Node* root) {
    if(dfs(root) == MINCOVERED)
        cameras++;

    return cameras;
}

int main() {
    struct Node* root = createNode(0);
    root->left = createNode(0);
    root->left->left = createNode(0);
    root->left->right = createNode(0);

    printf("Minimum Cameras Needed = %d\n", minCameraCover(root));

    return 0;
}

Day 61

#include <stdio.h>

#define MAX 100

int visited[MAX];
int isConnected[MAX][MAX];
int n;

void dfs(int city) {
    visited[city] = 1;

    for(int i = 0; i < n; i++) {
        if(isConnected[city][i] == 1 && !visited[i]) {
            dfs(i);
        }
    }
}

int main() {
    n = 5;

    int graph[5][5] = {
        {1, 1, 0, 0, 0},
        {1, 1, 0, 0, 0},
        {0, 0, 1, 1, 0},
        {0, 0, 1, 1, 0},
        {0, 0, 0, 0, 1}
    };

    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            isConnected[i][j] = graph[i][j];
        }
    }

    int provinces = 0;

    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            dfs(i);
            provinces++;
        }
    }

    printf("Number of Provinces = %d\n", provinces);

    return 0;
}

Day 62

#include <stdio.h>

#define MAX 100

int visited[MAX];
int rooms[MAX][MAX];
int roomSize[MAX];
int n;

void dfs(int room) {
    visited[room] = 1;

    for(int i = 0; i < roomSize[room]; i++) {
        int key = rooms[room][i];
        if(!visited[key]) {
            dfs(key);
        }
    }
}

int main() {
    n = 4;

    // Example:
    // room 0 has keys to 1,3
    // room 1 has key to 3
    // room 2 has no keys
    // room 3 has key to 0

    roomSize[0] = 2; rooms[0][0] = 1; rooms[0][1] = 3;
    roomSize[1] = 1; rooms[1][0] = 3;
    roomSize[2] = 0;
    roomSize[3] = 1; rooms[3][0] = 0;

    dfs(0);

    int allVisited = 1;

    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            allVisited = 0;
            break;
        }
    }

    if(allVisited)
        printf("All rooms can be visited\n");
    else
        printf("Not all rooms can be visited\n");

    return 0;
}

Day 63

#include <stdio.h>

int image[100][100];
int visited[100][100];

int n = 5, m = 5;

void floodFill(int x, int y, int oldColor, int newColor) {
    if(x < 0 || x >= n || y < 0 || y >= m)
        return;

    if(image[x][y] != oldColor || visited[x][y])
        return;

    visited[x][y] = 1;
    image[x][y] = newColor;

    floodFill(x + 1, y, oldColor, newColor);
    floodFill(x - 1, y, oldColor, newColor);
    floodFill(x, y + 1, oldColor, newColor);
    floodFill(x, y - 1, oldColor, newColor);
}

int main() {
    int i, j;

    int grid[5][5] = {
        {1, 1, 1, 2, 2},
        {1, 1, 0, 2, 2},
        {1, 0, 0, 2, 2},
        {1, 1, 1, 2, 2},
        {0, 0, 1, 1, 1}
    };

    for(i = 0; i < n; i++)
        for(j = 0; j < m; j++)
            image[i][j] = grid[i][j];

    floodFill(0, 0, 1, 9);

    printf("Flood Filled Image:\n");

    for(i = 0; i < n; i++) {
        for(j = 0; j < m; j++) {
            printf("%d ", image[i][j]);
        }
        printf("\n");
    }

    return 0;
}

Day 64

#include <stdio.h>

#define MAX 100

int grid[MAX][MAX];
int visited[MAX][MAX];

int n = 3, m = 3;

int dx[] = {1, -1, 0, 0};
int dy[] = {0, 0, 1, -1};

typedef struct {
    int x, y;
} Pair;

Pair queue[MAX * MAX];
int front = 0, rear = 0;

int isValid(int x, int y) {
    return x >= 0 && x < n && y >= 0 && y < m;
}

int main() {
    int i, j;
    int fresh = 0, time = 0;

    int g[3][3] = {
        {2, 1, 1},
        {1, 1, 0},
        {0, 1, 1}
    };

    for(i = 0; i < n; i++) {
        for(j = 0; j < m; j++) {
            grid[i][j] = g[i][j];
            if(grid[i][j] == 2) {
                queue[rear++] = (Pair){i, j};
                visited[i][j] = 1;
            }
            else if(grid[i][j] == 1) {
                fresh++;
            }
        }
    }

    while(front < rear && fresh > 0) {
        int size = rear - front;
        int rotten = 0;

        for(i = 0; i < size; i++) {
            Pair p = queue[front++];

            for(j = 0; j < 4; j++) {
                int nx = p.x + dx[j];
                int ny = p.y + dy[j];

                if(isValid(nx, ny) && !visited[nx][ny] && grid[nx][ny] == 1) {
                    grid[nx][ny] = 2;
                    visited[nx][ny] = 1;
                    queue[rear++] = (Pair){nx, ny};
                    fresh--;
                    rotten = 1;
                }
            }
        }

        if(rotten)
            time++;
    }

    if(fresh == 0)
        printf("Time required = %d\n", time);
    else
        printf("Not all oranges rot\n");

    return 0;
}

Day 65

#include <stdio.h>

#define MAX 100

int graph[MAX][MAX];
int visited[MAX];
int n;

int dfs(int node, int parent) {
    visited[node] = 1;

    for(int i = 0; i < n; i++) {
        if(graph[node][i]) {
            if(!visited[i]) {
                if(dfs(i, node))
                    return 1;
            }
            else if(i != parent) {
                return 1; // cycle detected
            }
        }
    }

    return 0;
}

int main() {
    n = 5;

    int g[5][5] = {
        {0, 1, 0, 0, 0},
        {1, 0, 1, 0, 0},
        {0, 1, 0, 1, 0},
        {0, 0, 1, 0, 1},
        {0, 0, 0, 1, 0}
    };

    for(int i = 0; i < n; i++)
        for(int j = 0; j < n; j++)
            graph[i][j] = g[i][j];

    int hasCycle = 0;

    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            if(dfs(i, -1)) {
                hasCycle = 1;
                break;
            }
        }
    }

    if(hasCycle)
        printf("Cycle Detected\n");
    else
        printf("No Cycle\n");

    return 0;
}

Day 66

#include <stdio.h>

#define MAX 100

int graph[MAX][MAX];
int visited[MAX];
int recStack[MAX];
int n;

int dfs(int node) {
    visited[node] = 1;
    recStack[node] = 1;

    for(int i = 0; i < n; i++) {
        if(graph[node][i]) {

            if(!visited[i]) {
                if(dfs(i))
                    return 1;
            }
            else if(recStack[i]) {
                return 1; // cycle found
            }
        }
    }

    recStack[node] = 0;
    return 0;
}

int main() {
    n = 4;

    // course dependencies (u -> v means u depends on v)
    int edges[4][2] = {
        {0, 1},
        {1, 2},
        {2, 3},
        {3, 1}   // cycle
    };

    for(int i = 0; i < 4; i++) {
        graph[edges[i][0]][edges[i][1]] = 1;
    }

    int hasCycle = 0;

    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            if(dfs(i)) {
                hasCycle = 1;
                break;
            }
        }
    }

    if(hasCycle)
        printf("Cannot finish courses\n");
    else
        printf("All courses can be finished\n");

    return 0;
}

Day 67

#include <stdio.h>

#define MAX 100

int graph[MAX][MAX];
int visited[MAX];
int recStack[MAX];
int order[MAX];
int idx = 0;

int n;

int dfs(int node) {
    visited[node] = 1;
    recStack[node] = 1;

    for(int i = 0; i < n; i++) {
        if(graph[node][i]) {

            if(!visited[i]) {
                if(dfs(i))
                    return 1;
            }
            else if(recStack[i]) {
                return 1; // cycle detected
            }
        }
    }

    recStack[node] = 0;
    order[idx++] = node; // add after processing
    return 0;
}

int main() {
    n = 4;

    int edges[4][2] = {
        {1, 0},
        {2, 0},
        {3, 1},
        {3, 2}
    };

    for(int i = 0; i < 4; i++) {
        graph[edges[i][0]][edges[i][1]] = 1;
    }

    int hasCycle = 0;

    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            if(dfs(i)) {
                hasCycle = 1;
                break;
            }
        }
    }

    if(hasCycle) {
        printf("No valid order (cycle exists)\n");
    } else {
        printf("Course Order:\n");

        for(int i = idx - 1; i >= 0; i--) {
            printf("%d ", order[i]);
        }
    }

    return 0;
}

Day 68

#include <stdio.h>

#define MAX 26

int graph[MAX][MAX];
int visited[MAX];
int stack[MAX];
int top = -1;

int n = 0;

void addEdge(char u, char v) {
    graph[u - 'a'][v - 'a'] = 1;
}

void dfs(int node) {
    visited[node] = 1;

    for(int i = 0; i < MAX; i++) {
        if(graph[node][i] && !visited[i]) {
            dfs(i);
        }
    }

    stack[++top] = node;
}

int main() {
    char words[][10] = {"wrt", "wrf", "er", "ett", "rftt"};
    int wordsCount = 5;

    for(int i = 0; i < wordsCount - 1; i++) {
        char *w1 = words[i];
        char *w2 = words[i + 1];

        int j = 0;

        while(w1[j] && w2[j] && w1[j] == w2[j])
            j++;

        if(w1[j] && w2[j]) {
            addEdge(w1[j], w2[j]);
        }
    }

    for(int i = 0; i < MAX; i++) {
        if(!visited[i]) {
            dfs(i);
        }
    }

    printf("Alien Dictionary Order:\n");

    for(int i = top; i >= 0; i--) {
        printf("%c ", stack[i] + 'a');
    }

    return 0;
}

Day 69

#include <stdio.h>

#define MAX 100
#define INF 1000000

int graph[MAX][MAX];
int dist[MAX];
int visited[MAX];
int n;

int minDistance() {
    int min = INF, minIndex = -1;

    for(int i = 0; i < n; i++) {
        if(!visited[i] && dist[i] < min) {
            min = dist[i];
            minIndex = i;
        }
    }

    return minIndex;
}

int main() {
    n = 4;

    // adjacency matrix (directed weighted graph)
    int edges[4][3] = {
        {0, 1, 1},
        {1, 2, 2},
        {0, 2, 4},
        {2, 3, 1}
    };

    for(int i = 0; i < n; i++)
        for(int j = 0; j < n; j++)
            graph[i][j] = (i == j) ? 0 : INF;

    for(int i = 0; i < 4; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        int w = edges[i][2];
        graph[u][v] = w;
    }

    for(int i = 0; i < n; i++) {
        dist[i] = INF;
        visited[i] = 0;
    }

    int source = 0;
    dist[source] = 0;

    for(int count = 0; count < n - 1; count++) {
        int u = minDistance();
        visited[u] = 1;

        for(int v = 0; v < n; v++) {
            if(!visited[v] && graph[u][v] != INF &&
               dist[u] != INF &&
               dist[u] + graph[u][v] < dist[v]) {
                dist[v] = dist[u] + graph[u][v];
            }
        }
    }

    int maxTime = 0;

    for(int i = 0; i < n; i++) {
        if(dist[i] == INF) {
            printf("Not all nodes reachable\n");
            return 0;
        }
        if(dist[i] > maxTime)
            maxTime = dist[i];
    }

    printf("Network Delay Time = %d\n", maxTime);

    return 0;
}

Day 70

#include <stdio.h>

#define MAX 100
#define INF 100000000

int n = 4;
int graph[MAX][MAX];

int minCost = INF;

void dfs(int src, int dst, int stops, int cost) {
    if(cost >= minCost)
        return;

    if(src == dst) {
        minCost = cost;
        return;
    }

    if(stops < 0)
        return;

    for(int i = 0; i < n; i++) {
        if(graph[src][i] != INF) {
            dfs(i, dst, stops - 1, cost + graph[src][i]);
        }
    }
}

int main() {
    int edges[5][3] = {
        {0, 1, 100},
        {1, 2, 100},
        {0, 2, 500},
        {2, 3, 100},
        {1, 3, 600}
    };

    for(int i = 0; i < n; i++)
        for(int j = 0; j < n; j++)
            graph[i][j] = INF;

    for(int i = 0; i < 5; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        int w = edges[i][2];
        graph[u][v] = w;
    }

    int src = 0, dst = 3, K = 1;

    dfs(src, dst, K, 0);

    if(minCost == INF)
        printf("No route within %d stops\n", K);
    else
        printf("Cheapest Price = %d\n", minCost);

    return 0;
}

Day 71

#include <stdio.h>
#include <stdlib.h>

#define MAX 100
#define INF 100000000

int n = 4;

int parent[MAX];

int find(int i) {
    if(parent[i] == i)
        return i;
    return parent[i] = find(parent[i]);
}

void unionSet(int a, int b) {
    parent[find(a)] = find(b);
}

int absVal(int x) {
    return x < 0 ? -x : x;
}

int main() {
    int points[4][2] = {
        {0, 0},
        {2, 2},
        {3, 10},
        {5, 2}
    };

    int edges[MAX][3];
    int e = 0;

    // Build all edges (Manhattan distance)
    for(int i = 0; i < n; i++) {
        for(int j = i + 1; j < n; j++) {
            int dist = absVal(points[i][0] - points[j][0]) +
                       absVal(points[i][1] - points[j][1]);

            edges[e][0] = i;
            edges[e][1] = j;
            edges[e][2] = dist;
            e++;
        }
    }

    // Sort edges (simple bubble sort)
    for(int i = 0; i < e - 1; i++) {
        for(int j = 0; j < e - i - 1; j++) {
            if(edges[j][2] > edges[j + 1][2]) {
                int t0 = edges[j][0];
                int t1 = edges[j][1];
                int t2 = edges[j][2];

                edges[j][0] = edges[j + 1][0];
                edges[j][1] = edges[j + 1][1];
                edges[j][2] = edges[j + 1][2];

                edges[j + 1][0] = t0;
                edges[j + 1][1] = t1;
                edges[j + 1][2] = t2;
            }
        }
    }

    for(int i = 0; i < n; i++)
        parent[i] = i;

    int cost = 0, count = 0;

    for(int i = 0; i < e && count < n - 1; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        int w = edges[i][2];

        if(find(u) != find(v)) {
            unionSet(u, v);
            cost += w;
            count++;
        }
    }

    printf("Minimum Cost to Connect All Points = %d\n", cost);

    return 0;
}

Day 72

#include <stdio.h>

#define MAX 10
#define INF 100000000

int n = 4;
int graph[MAX][MAX];

int visited[MAX];

int minCost = INF;

void tsp(int curr, int count, int cost, int start) {
    if(count == n && graph[curr][start] != 0) {
        int totalCost = cost + graph[curr][start];
        if(totalCost < minCost)
            minCost = totalCost;
        return;
    }

    for(int i = 0; i < n; i++) {
        if(!visited[i] && graph[curr][i] != 0) {
            visited[i] = 1;
            tsp(i, count + 1, cost + graph[curr][i], start);
            visited[i] = 0;
        }
    }
}

int main() {
    int i, j;

    int g[4][4] = {
        {0, 10, 15, 20},
        {10, 0, 35, 25},
        {15, 35, 0, 30},
        {20, 25, 30, 0}
    };

    for(i = 0; i < n; i++)
        for(j = 0; j < n; j++)
            graph[i][j] = g[i][j];

    visited[0] = 1;
    tsp(0, 1, 0, 0);

    printf("Minimum Cost of TSP = %d\n", minCost);

    return 0;
}

Day 73

#include <stdio.h>

#define MAX 100

int parent[MAX];
int n = 5;

int find(int x) {
    if(parent[x] == x)
        return x;
    return parent[x] = find(parent[x]);
}

int unionSet(int a, int b) {
    int pa = find(a);
    int pb = find(b);

    if(pa == pb)
        return 1; // redundant edge

    parent[pa] = pb;
    return 0;
}

int main() {
    int edges[5][2] = {
        {1, 2},
        {1, 3},
        {2, 3}, // redundant
        {3, 4},
        {4, 5}
    };

    for(int i = 1; i <= n; i++)
        parent[i] = i;

    for(int i = 0; i < 5; i++) {
        int u = edges[i][0];
        int v = edges[i][1];

        if(unionSet(u, v)) {
            printf("Redundant Connection = [%d, %d]\n", u, v);
            break;
        }
    }

    return 0;
}

Day 74

#include <stdio.h>

#define MAX 100

int graph[MAX][MAX];
int visited[MAX];
int n;

void dfs(int node) {
    visited[node] = 1;

    for(int i = 0; i < n; i++) {
        if(graph[node][i] && !visited[i]) {
            dfs(i);
        }
    }
}

int main() {
    n = 5;

    int edges[4][2] = {
        {0, 1},
        {1, 2},
        {3, 4}
    };

    // build adjacency matrix
    for(int i = 0; i < n; i++)
        for(int j = 0; j < n; j++)
            graph[i][j] = 0;

    for(int i = 0; i < 4; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        graph[u][v] = 1;
        graph[v][u] = 1;
    }

    int components = 0;

    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            dfs(i);
            components++;
        }
    }

    printf("Number of Connected Components = %d\n", components);

    return 0;
}

Day 75

#include <stdio.h>

#define MAX 100

int graph[MAX][MAX];
int color[MAX];
int n;

int dfs(int node, int c) {
    color[node] = c;

    for(int i = 0; i < n; i++) {
        if(graph[node][i]) {

            if(color[i] == -1) {
                if(!dfs(i, 1 - c))
                    return 0;
            }
            else if(color[i] == c) {
                return 0; // same color on both sides
            }
        }
    }

    return 1;
}

int main() {
    n = 4;

    int edges[4][2] = {
        {0, 1},
        {1, 2},
        {2, 3},
        {3, 0} // even cycle -> bipartite
    };

    for(int i = 0; i < n; i++)
        for(int j = 0; j < n; j++)
            graph[i][j] = 0;

    for(int i = 0; i < 4; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        graph[u][v] = 1;
        graph[v][u] = 1;
    }

    for(int i = 0; i < n; i++)
        color[i] = -1;

    int isBipartite = 1;

    for(int i = 0; i < n; i++) {
        if(color[i] == -1) {
            if(!dfs(i, 0)) {
                isBipartite = 0;
                break;
            }
        }
    }

    if(isBipartite)
        printf("Graph is Bipartite\n");
    else
        printf("Graph is NOT Bipartite\n");

    return 0;
}

Day 76

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

struct Node {
    int val;
    int neighbors[MAX];
    int size;
};

struct Node* clone[MAX];
int visited[MAX];

struct Node* createNode(int val) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->val = val;
    newNode->size = 0;
    return newNode;
}

void dfs(struct Node* node) {
    if(node == NULL) return;

    visited[node->val] = 1;

    if(clone[node->val] == NULL)
        clone[node->val] = createNode(node->val);

    for(int i = 0; i < node->size; i++) {
        int nei = node->neighbors[i];

        if(clone[nei] == NULL)
            clone[nei] = createNode(nei);

        clone[node->val]->neighbors[clone[node->val]->size++] = nei;

        if(!visited[nei]) {
            dfs(clone[nei]);
        }
    }
}

int main() {
    struct Node* node0 = createNode(0);
    struct Node* node1 = createNode(1);
    struct Node* node2 = createNode(2);

    node0->neighbors[node0->size++] = 1;
    node0->neighbors[node0->size++] = 2;

    node1->neighbors[node1->size++] = 0;

    node2->neighbors[node2->size++] = 0;

    dfs(node0);

    printf("Graph cloned successfully\n");

    return 0;
}

Day 77

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

int graph[MAX][MAX];
int visited[MAX];
int disc[MAX], low[MAX];
int parent[MAX];
int n;
int timer = 0;

void dfs(int u) {
    visited[u] = 1;
    disc[u] = low[u] = ++timer;

    for(int v = 0; v < n; v++) {
        if(graph[u][v]) {

            if(!visited[v]) {
                parent[v] = u;

                dfs(v);

                if(low[v] < low[u])
                    low[u] = low[v];

                // Bridge condition
                if(low[v] > disc[u]) {
                    printf("Critical Connection: %d - %d\n", u, v);
                }
            }
            else if(v != parent[u]) {
                if(disc[v] < low[u])
                    low[u] = disc[v];
            }
        }
    }
}

int main() {
    n = 5;

    int edges[5][2] = {
        {0, 1},
        {1, 2},
        {2, 0},
        {1, 3},
        {3, 4}
    };

    for(int i = 0; i < n; i++) {
        visited[i] = 0;
        parent[i] = -1;
    }

    for(int i = 0; i < 5; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        graph[u][v] = 1;
        graph[v][u] = 1;
    }

    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            dfs(i);
        }
    }

    return 0;
}

Day 78

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

int graph[MAX][MAX];
int visited[MAX];
int disc[MAX], low[MAX];
int parent[MAX];
int isAP[MAX];

int n;
int timer = 0;

void dfs(int u) {
    visited[u] = 1;
    disc[u] = low[u] = ++timer;

    int children = 0;

    for(int v = 0; v < n; v++) {
        if(graph[u][v]) {

            if(!visited[v]) {
                children++;
                parent[v] = u;

                dfs(v);

                if(low[v] < low[u])
                    low[u] = low[v];

                // articulation point condition (non-root)
                if(parent[u] != -1 && low[v] >= disc[u])
                    isAP[u] = 1;
            }
            else if(v != parent[u]) {
                if(disc[v] < low[u])
                    low[u] = disc[v];
            }
        }
    }

    // root condition
    if(parent[u] == -1 && children > 1)
        isAP[u] = 1;
}

int main() {
    n = 5;

    int edges[5][2] = {
        {0, 1},
        {1, 2},
        {2, 0},
        {1, 3},
        {3, 4}
    };

    for(int i = 0; i < n; i++) {
        visited[i] = 0;
        parent[i] = -1;
        isAP[i] = 0;
    }

    for(int i = 0; i < 5; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        graph[u][v] = 1;
        graph[v][u] = 1;
    }

    for(int i = 0; i < n; i++) {
        if(!visited[i]) {
            dfs(i);
        }
    }

    printf("Articulation Points:\n");

    for(int i = 0; i < n; i++) {
        if(isAP[i])
            printf("%d ", i);
    }

    return 0;
}

Day 79

#include <stdio.h>

#define MAX 100

int graph[MAX][MAX];
int transpose[MAX][MAX];
int visited[MAX];
int stack[MAX];
int top = -1;
int n;

void dfs1(int v) {
    visited[v] = 1;

    for(int i = 0; i < n; i++) {
        if(graph[v][i] && !visited[i]) {
            dfs1(i);
        }
    }

    stack[++top] = v;
}

void dfs2(int v) {
    visited[v] = 1;
    printf("%d ", v);

    for(int i = 0; i < n; i++) {
        if(transpose[v][i] && !visited[i]) {
            dfs2(i);
        }
    }
}

int main() {
    n = 5;

    int edges[6][2] = {
        {0, 2},
        {2, 1},
        {1, 0},
        {0, 3},
        {3, 4},
        {4, 3}
    };

    // initialize matrices
    for(int i = 0; i < n; i++) {
        visited[i] = 0;
        for(int j = 0; j < n; j++) {
            graph[i][j] = 0;
            transpose[i][j] = 0;
        }
    }

    for(int i = 0; i < 6; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        graph[u][v] = 1;
    }

    // step 1: fill order stack
    for(int i = 0; i < n; i++) {
        if(!visited[i])
            dfs1(i);
    }

    // step 2: transpose graph
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            if(graph[i][j])
                transpose[j][i] = 1;
        }
    }

    // reset visited
    for(int i = 0; i < n; i++)
        visited[i] = 0;

    printf("Strongly Connected Components:\n");

    // step 3: process stack
    while(top != -1) {
        int v = stack[top--];

        if(!visited[v]) {
            dfs2(v);
            printf("\n");
        }
    }

    return 0;
}

Day 80

#include <stdio.h>

#define MAX 100
#define INF 100000000

int dist[MAX][MAX];
int n;

int main() {
    n = 4;

    int edges[4][3] = {
        {0, 1, 3},
        {1, 2, 1},
        {1, 3, 4},
        {2, 3, 1}
    };

    // initialize distance matrix
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            if(i == j)
                dist[i][j] = 0;
            else
                dist[i][j] = INF;
        }
    }

    for(int i = 0; i < 4; i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        int w = edges[i][2];

        dist[u][v] = w;
        dist[v][u] = w;
    }

    // Floyd Warshall
    for(int k = 0; k < n; k++) {
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < n; j++) {
                if(dist[i][k] + dist[k][j] < dist[i][j]) {
                    dist[i][j] = dist[i][k] + dist[k][j];
                }
            }
        }
    }

    int threshold = 4;
    int bestCity = -1;
    int minReachable = INF;

    for(int i = 0; i < n; i++) {
        int count = 0;

        for(int j = 0; j < n; j++) {
            if(i != j && dist[i][j] <= threshold)
                count++;
        }

        if(count <= minReachable) {
            minReachable = count;
            bestCity = i;
        }
    }

    printf("City with smallest number of neighbors = %d\n", bestCity);

    return 0;
}

Day 81

#include <stdio.h>

int binarySearch(int arr[], int n, int target) {
    int low = 0, high = n - 1;

    while(low <= high) {
        int mid = low + (high - low) / 2;

        if(arr[mid] == target)
            return mid;

        if(arr[mid] < target)
            low = mid + 1;
        else
            high = mid - 1;
    }

    return -1;
}

int main() {
    int arr[] = {2, 5, 8, 12, 16, 23, 38, 56, 72, 91};
    int n = 10;
    int target = 23;

    int result = binarySearch(arr, n, target);

    if(result != -1)
        printf("Element found at index %d\n", result);
    else
        printf("Element not found\n");

    return 0;
}
Day 82

#include <stdio.h>

int searchInsert(int arr[], int n, int target) {
    int low = 0, high = n - 1;

    while(low <= high) {
        int mid = low + (high - low) / 2;

        if(arr[mid] == target)
            return mid;

        if(arr[mid] < target)
            low = mid + 1;
        else
            high = mid - 1;
    }

    return low; // correct insert position
}

int main() {
    int arr[] = {1, 3, 5, 6};
    int n = 4;
    int target = 5;

    printf("Insert Position = %d\n", searchInsert(arr, n, target));

    target = 2;
    printf("Insert Position = %d\n", searchInsert(arr, n, target));

    return 0;
}

Day 83

#include <stdio.h>

int search(int arr[], int n, int target) {
    int low = 0, high = n - 1;

    while(low <= high) {
        int mid = low + (high - low) / 2;

        if(arr[mid] == target)
            return mid;

        // left half sorted
        if(arr[low] <= arr[mid]) {
            if(target >= arr[low] && target < arr[mid])
                high = mid - 1;
            else
                low = mid + 1;
        }
        // right half sorted
        else {
            if(target > arr[mid] && target <= arr[high])
                low = mid + 1;
            else
                high = mid - 1;
        }
    }

    return -1;
}

int main() {
    int arr[] = {4, 5, 6, 7, 0, 1, 2};
    int n = 7;
    int target = 0;

    int res = search(arr, n, target);

    if(res != -1)
        printf("Element found at index %d\n", res);
    else
        printf("Element not found\n");

    return 0;
}

Day 84

#include <stdio.h>

int findPeak(int arr[], int n) {
    int low = 0, high = n - 1;

    while(low < high) {
        int mid = low + (high - low) / 2;

        if(arr[mid] < arr[mid + 1])
            low = mid + 1;
        else
            high = mid;
    }

    return low;
}

int main() {
    int arr[] = {1, 2, 3, 1};
    int n = 4;

    int peakIndex = findPeak(arr, n);

    printf("Peak Element = %d at index %d\n", arr[peakIndex], peakIndex);

    return 0;
}

Day 85

#include <stdio.h>

int findMin(int arr[], int n) {
    int low = 0, high = n - 1;

    while(low < high) {
        int mid = low + (high - low) / 2;

        if(arr[mid] > arr[high])
            low = mid + 1;
        else
            high = mid;
    }

    return arr[low];
}

int main() {
    int arr[] = {4, 5, 6, 7, 0, 1, 2};
    int n = 7;

    printf("Minimum element = %d\n", findMin(arr, n));

    return 0;
}


Day 86#include <stdio.h>

int mySqrt(int x) {
    long long low = 0, high = x, ans = 0;

    while(low <= high) {
        long long mid = low + (high - low) / 2;
        long long sq = mid * mid;

        if(sq == x)
            return mid;

        if(sq < x) {
            ans = mid;
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    return ans;
}

int main() {
    int x = 17;

    printf("Square root (floor) = %d\n", mySqrt(x));

    return 0;
}


Day 87

#include <stdio.h>

int canEatAll(int piles[], int n, int h, int k) {
    long long hours = 0;

    for(int i = 0; i < n; i++) {
        hours += piles[i] / k;
        if(piles[i] % k != 0)
            hours++;
    }

    return hours <= h;
}

int minEatingSpeed(int piles[], int n, int h) {
    int low = 1, high = 0;

    for(int i = 0; i < n; i++) {
        if(piles[i] > high)
            high = piles[i];
    }

    int ans = high;

    while(low <= high) {
        int mid = low + (high - low) / 2;

        if(canEatAll(piles, n, h, mid)) {
            ans = mid;
            high = mid - 1;
        } else {
            low = mid + 1;
        }
    }

    return ans;
}

int main() {
    int piles[] = {3, 6, 7, 11};
    int n = 4;
    int h = 8;

    printf("Minimum eating speed = %d\n", minEatingSpeed(piles, n, h));

    return 0;
}






