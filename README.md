#include <stdio.h>

int main() {
    int n;

    printf("Enter number of terms: ");
    scanf("%d", &n);

    int a = 0, b = 1, next;

    printf("Fibonacci Series:\n");

    for(int i = 1; i <= n; i++) {
        printf("%d ", a);
        next = a + b;
        a = b;
        b = next;
    }

    return 0;
}