#include <stdio.h>

int main() {
    int i, j, n, m;
    printf("Enter number of processes: ");
    scanf("%d", &n);
    printf("Enter number of resource types: ");
    scanf("%d", &m);

    int alloc[n][m], max[n][m], need[n][m], avail[m];
    int finish[n], safeSeq[n];

    printf("Enter Allocation Matrix:\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < m; j++)
            scanf("%d", &alloc[i][j]);

    printf("Enter Maximum Matrix:\n");
    for (i = 0; i < n; i++)
        for (j = 0; j < m; j++)
            scanf("%d", &max[i][j]);

    printf("Enter Available Resources:\n");
    for (j = 0; j < m; j++)
        scanf("%d", &avail[j]);

    // Calculate Need
    for (i = 0; i < n; i++)
        for (j = 0; j < m; j++)
            need[i][j] = max[i][j] - alloc[i][j];

    for (i = 0; i < n; i++)
        finish[i] = 0;

    int count = 0;
    while (count < n) {
        int found = 0;
        for (i = 0; i < n; i++) {
            if (finish[i] == 0) {
                int canRun = 1;
                for (j = 0; j < m; j++) {
                    if (need[i][j] > avail[j]) {
                        canRun = 0;
                        break;
                    }
                }
                if (canRun) {
                    for (j = 0; j < m; j++)
                        avail[j] += alloc[i][j];

                    safeSeq[count++] = i;
                    finish[i] = 1;
                    found = 1;
                }
            }
        }
        if (!found) {
            printf("System is not in a safe state.\n");
            return 1;
        }
    }

    printf("System is in a safe state.\nSafe sequence: ");
    for (i = 0; i < n; i++)
        printf("P%d ", safeSeq[i]);
    printf("\n");
    return 0;
}
