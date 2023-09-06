#include <stdio.h>

int main() {
    const int MOD = 12345;
    int n = 210;
    int dp[n + 1];
    
    dp[0] = 1;
    dp[1] = 2;
    dp[2] = 4;
    
    for (int i = 3; i <= n; i++) {
        dp[i] = (dp[i - 1] + dp[i - 2] - dp[i - 3] + MOD) % MOD;
    }
    
    printf("%d\n", dp[n]);
    
    return 0;
}
