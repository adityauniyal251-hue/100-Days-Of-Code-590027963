# 100-Days-Of-Code-590027963


1) #include <stdio.h>

int main() {
    int n, pos, x, arr[100];

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    scanf("%d %d", &pos, &x);

    for(int i = n; i >= pos; i--)
        arr[i] = arr[i - 1];

    arr[pos - 1] = x;

    for(int i = 0; i <= n; i++)
        printf("%d ", arr[i]);

    return 0;
}


2) #include <stdio.h>

int main() {
    int n, pos, arr[100];

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    scanf("%d", &pos);

    for(int i = pos - 1; i < n - 1; i++)
        arr[i] = arr[i + 1];

    for(int i = 0; i < n - 1; i++)
        printf("%d ", arr[i]);

    return 0;
}


3)  #include <stdio.h>

int main() {
    int n, arr[100];

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    for(int i = 0; i < n/2; i++) {
        int temp = arr[i];
        arr[i] = arr[n - i - 1];
        arr[n - i - 1] = temp;
    }

    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);

    return 0;
}

4)  #include <stdio.h>

int main() {
    int n, arr[100], max;

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    max = arr[0];

    for(int i = 1; i < n; i++) {
        if(arr[i] > max)
            max = arr[i];
    }

    printf("%d", max);

    return 0;
}

5)  #include <stdio.h>

int main() {
    int n, arr[100], min;

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    min = arr[0];

    for(int i = 1; i < n; i++) {
        if(arr[i] < min)
            min = arr[i];
    }

    printf("%d", min);

    return 0;
}

6)  #include <stdio.h>

int main() {
    int n, arr[100], key, found = 0;

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    scanf("%d", &key);

    for(int i = 0; i < n; i++) {
        if(arr[i] == key) {
            printf("%d", i);  
            found = 1;
            break;
        }
    }

    if(found == 0)
        printf("-1");

    return 0;
}

7)  #include <stdio.h>

int main() {
    int n, arr[100], key;
    int low = 0, high, mid, found = 0;

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    scanf("%d", &key);

    high = n - 1;

    while(low <= high) {
        mid = (low + high) / 2;

        if(arr[mid] == key) {
            printf("%d", mid);
            found = 1;
            break;
        }
        else if(arr[mid] < key)
            low = mid + 1;
        else
            high = mid - 1;
    }

    if(found == 0)
        printf("-1");

    return 0;
}

8)  #include <stdio.h>

int main() {
    int n, arr[100];

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    for(int i = 0; i < n - 1; i++) {
        for(int j = 0; j < n - i - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);

    return 0;
}


9)  #include <stdio.h>

int main() {
    int n, arr[100];

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    for(int i = 0; i < n - 1; i++) {
        int min = i;

        for(int j = i + 1; j < n; j++) {
            if(arr[j] < arr[min])
                min = j;
        }

        int temp = arr[i];
        arr[i] = arr[min];
        arr[min] = temp;
    }

    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);

    return 0;
}


10)  #include <stdio.h>

int main() {
    int n, arr[100];

    scanf("%d", &n);
    for(int i = 0; i < n; i++)
        scanf("%d", &arr[i]);

    for(int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;

        while(j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }

        arr[j + 1] = key;
    }

    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);

    return 0;
}
