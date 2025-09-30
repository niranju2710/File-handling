 #include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *fp;
    char data[100];

    // Open file for writing
    fp = fopen("sample.txt", "w");
    if (fp == NULL) {
        perror("Error opening file");
        return 1;
    }

    printf("Enter text to write into the file: ");
    if (fgets(data, sizeof(data), stdin) == NULL) {
        printf("Error reading input.\n");
        fclose(fp);
        return 1;
    }

    fprintf(fp, "%s", data);
    fclose(fp);
    printf("Data written successfully.\n");

    // Open file for reading
    fp = fopen("sample.txt", "r");
    if (fp == NULL) {
        perror("Error opening file");
        return 1;
    }

    printf("\nReading from file:\n");
    while (fgets(data, sizeof(data), fp) != NULL) {
        printf("%s", data);
    }

    fclose(fp);
    return 0;
}
