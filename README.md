// Lab 2: Arrays - Binary Search
// Iterative and recursive binary search
#include <iostream>
using namespace std;

int binarySearchIterative(const int arr[], int size, int key) {
    int low = 0, high = size - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key) return mid;
        if (key < arr[mid]) high = mid - 1;
        else low = mid + 1;
    }
    return -1;
}

int binarySearchRecursive(const int arr[], int low, int high, int key) {
    if (low > high) return -1;
    int mid = low + (high - low) / 2;
    if (arr[mid] == key) return mid;
    if (key < arr[mid])
        return binarySearchRecursive(arr, low, mid - 1, key);
    return binarySearchRecursive(arr, mid + 1, high, key);
}

void displayArray(const int arr[], int size) {
    for (int i = 0; i < size; ++i) cout << arr[i] << " ";
    cout << '\n';
}

int main() {
    int arr[] = {10, 20, 30, 40, 50, 60, 70};
    int size = sizeof(arr) / sizeof(arr[0]);
    int key;

    cout << "Sorted array: ";
    displayArray(arr, size);
    cout << "Enter value to search: ";
    cin >> key;

    int iterativeResult = binarySearchIterative(arr, size, key);
    int recursiveResult = binarySearchRecursive(arr, 0, size - 1, key);

    if (iterativeResult != -1)
        cout << "Iterative search: found at index " << iterativeResult << '\n';
    else
        cout << "Iterative search: value not found\n";

    if (recursiveResult != -1)
        cout << "Recursive search: found at index " << recursiveResult << '\n';
    else
        cout << "Recursive search: value not found\n";

    return 0;
}
