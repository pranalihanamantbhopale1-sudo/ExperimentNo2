# Experiment No. 2

## Title
**Quick Sort and Merge Sort Using Array as a Data Structure**

### Analyse Time and Space Complexity

### Student Details
- **Email:** pranalihanamantbhopale1@gmail.com
- **GitHub:** https://github.com/pranalihanamantbhopale1-sudo/ExperimentNo2

---

## Aim

To implement **Quick Sort** and **Merge Sort** using arrays and analyze their time and space complexity.

---

## Program

```c
#include <stdio.h>

void quickSort(int arr[], int low, int high)
{
    if (low < high)
    {
        int pivot = arr[high];
        int i = (low - 1);

        for (int j = low; j < high; j++)
        {
            if (arr[j] <= pivot)
            {
                i++;
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }

        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        int pi = i + 1;

        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

void merge(int arr[], int low, int mid, int high)
{
    int n1 = mid - low + 1;
    int n2 = high - mid;

    int L[n1], R[n2];

    for (int i = 0; i < n1; i++)
        L[i] = arr[low + i];

    for (int j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];

    int i = 0, j = 0, k = low;

    while (i < n1 && j < n2)
    {
        if (L[i] <= R[j])
            arr[k++] = L[i++];
        else
            arr[k++] = R[j++];
    }

    while (i < n1)
        arr[k++] = L[i++];

    while (j < n2)
        arr[k++] = R[j++];
}

void mergeSort(int arr[], int low, int high)
{
    if (low < high)
    {
        int mid = (low + high) / 2;

        mergeSort(arr, low, mid);
        mergeSort(arr, mid + 1, high);
        merge(arr, low, mid, high);
    }
}

int main()
{
    int n, i;

    printf("Enter size of array: ");
    scanf("%d", &n);

    int arr[n], arrCopy[n];

    printf("Enter %d elements: ", n);

    for (i = 0; i < n; i++)
    {
        scanf("%d", &arr[i]);
        arrCopy[i] = arr[i];
    }

    quickSort(arr, 0, n - 1);

    printf("Array after Quick Sort: ");
    for (i = 0; i < n; i++)
        printf("%d ", arr[i]);

    printf("\n");

    mergeSort(arrCopy, 0, n - 1);

    printf("Array after Merge Sort: ");
    for (i = 0; i < n; i++)
        printf("%d ", arrCopy[i]);

    printf("\n");

    return 0;
}
```

---

## Output

> Save the output image in your repository as **output_quick_merge_sort.jpeg**

<img width="1600" height="534" alt="output_quick_merge_sort" src="output_quick_merge_sort.jpeg">

---

## Time and Space Complexity

| Algorithm | Best | Average | Worst | Space |
|-----------|------|---------|-------|-------|
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) |

---

## Applications

1. Used in sorting operations in system libraries and compilers.
2. Commonly applied in database query optimization and data indexing.
3. Merge Sort is preferred in external sorting for large datasets stored on disk.
4. Quick Sort is used in real-time applications where memory usage must be minimized.
5. Both algorithms are employed in data preprocessing for machine learning models.
6. Merge Sort is useful in parallel computing due to its predictable structure.
7. Quick Sort is applied in embedded systems where space optimization is important.

---

## Conclusion

Quick Sort and Merge Sort are efficient divide-and-conquer sorting algorithms. **Quick Sort** is generally faster for in-memory sorting with low extra space, while **Merge Sort** guarantees **O(n log n)** performance and is ideal for large and external datasets due to its stable sorting behavior.
