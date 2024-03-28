#include <stdio.h>

int countSequences(int n) {
    int mod = 12345;
    int a[n+1], b[n+1], c[n+1];
    
    a[1] = 1;
    b[1] = 1;
    c[1] = 0;
    
    for (int i = 2; i <= n; i++) {
        a[i] = (a[i-1] + b[i-1]) % mod;
        b[i] = (a[i-1] + b[i-1] + c[i-1]) % mod;
        c[i] = b[i-1];
    }
    
    return (a[n] + b[n] + c[n]) % mod;
}

int main() {
    int n;
    printf("Введіть довжину послідовностей n: ");
    scanf("%d", &n);
    
    if (n < 1 || n >= 10000) {
        printf("Неправильне значення n.\n");
        return 1;
    }
    
    int result = countSequences(n);
    printf("Кількість шуканих послідовностей за модулем 12345: %d\n", result);
    
    return 0;
}
