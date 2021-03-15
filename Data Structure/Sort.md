<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Sort](#sort)
  - [Insertion Sort](#insertion-sort)
    - [Straight Insertion Sort](#straight-insertion-sort)
    - [Binary Insertion Sort](#binary-insertion-sort)
    - [Shell's Sort(Diminishing Increment Sort)](#shells-sortdiminishing-increment-sort)
  - [Swap Sort](#swap-sort)
    - [Bubble Sort](#bubble-sort)
    - [Quick Sort](#quick-sort)
  - [Selection Sort](#selection-sort)
    - [Simple Selection Sort](#simple-selection-sort)
    - [HeapSort](#heapsort)
  - [Merge Sort](#merge-sort)
    - [Binary Merge Sort](#binary-merge-sort)
  - [Radix Sort(Bucket Sort/Bin Sort)](#radix-sortbucket-sortbin-sort)
  - [External Sort](#external-sort)
    - [Swap-Select Sort](#swap-select-sort)
    - [Best Merge Tree](#best-merge-tree)
    - [Loser Tree](#loser-tree)

<!-- /code_chunk_output -->

# Sort

## Insertion Sort

### Straight Insertion Sort
```c {.line-numbers}
void InsertSort(int R[], int n){
    int i, j;
    int temp;
    for(i=1; i<n; ++i){
        temp=R[i];
        j=i-1;
        while(j>=0 && temp<R[j]){
            R[j+1]=R[i];
            --j;
        }
        R[j+1]=temp;
    }
}
```

Time complexity: O(n) < **O(n^2^)** < O(n^2^)
Space complexity: O(1)

### Binary Insertion Sort
Time complexity: O(nlog~2~n) < **O(n^2^)** < O(n^2^)
Space complexity: O(1)

### Shell's Sort(Diminishing Increment Sort)
**Selection of Increment:**
1. Papernov & Stasevich
    2^k^+1, ..., 5, 3, 1
2. Shell
    n/2^k^, ..., 2, 1(down)

Time complexity: O(n^3/2^) < O(n^2^)
Space complexity: O(1)

## Swap Sort

### Bubble Sort
```c {.line-numbers}
void BubbleSort(int R[], int n){
    int i, j, flag;
    int temp;
    for(i=n-1; i>=1; --i){
        flag=0;
        for(j=1; j<=i; ++j)
            if(R[j-i]>R[j]){
                temp=R[j];
                R[j]=R[j-1];
                R[j-1]=temp;
                flag=1;
            }
        if(flag=0)
            return;
    }
}
```
Time complexity: O(n) < **O(n^2^)** < O(n^2^)
Space complexity: O(1)

### Quick Sort
```c {.line-numbers}
void QuickSort(int R[], int low, int high){
    int temp;
    int i=low, j=high;
    if(low<high){
        temp=R[low];
        while(i<j){
            while(j>i && R[j]>=temp)
                --j;
            if(i<j){
                R[i]=R[j];
                ++i;
            }
            while(j>i && R[i]<temp)
                ++i;
            if(i<j){
                R[j]=R[i];
                --j;
            }
        }
        R[i]=temp;
        QuickSort(R, low, i);
        QuickSort(R, i+1, high);
    }
}
```

Time complexity: O(nlog~2~n) < **O(nlog~2~n)** < O(n^2^)
Space complexity: O(log~2~n)

## Selection Sort

### Simple Selection Sort
```c {.line-numbers}
void SelectSort(int R[], int n){
    int i, j, k;
    int temp;
    for(i=0; i<n; ++i){
        k=i;
        for(j=i+1; j<n; ++j)
            if(R[k]>R[j])
                k=j;
        temp=R[i];
        R[i]=R[k];
        R[k]=temp;
    }
}
```

Time complexity: **O(n^2^)**
Space complexity: O(1)

### HeapSort
```c {.line-numbers}
void Sift(int R[], int low, int high){
    int i=low, j=2*i;
    int temp=R[i];
    while(j<=high){
        if(j<=high && R[j]<R[j+1])
            ++j;
        if(temp<R[j]){
            R[i]=R[j];
            i=j;
            j=2*i;
        }else
            break;
    }
    R[i]=temp;
}

void heapsort(int R[], int n){
    int i;
    int temp;
    for(i=n/2; i>=1; --i)
        Sift(R, i, n);
    for(i=n; i>=2; --i){
        temp=R[1];
        R[1]=R[i];
        R[i]=temp;
        Sift(R, 1, i-1);
    }
}
```

Time complexity: **O(nlog~2~n)** < O(nlog~2~n)
Space complexity: O(1)

## Merge Sort

### Binary Merge Sort
```c {.line-numbers}
void mergeSort(int A[], int low, int high){
    if(low<high){
        int mid=(low+high)/2;
        mergeSort(A, low, mid);
        mergeSort(A, mid+1, high);
        merge(A, low, mid, high);
    }
}
```

Time complexity: **O(nlog~2~n)**
Space complexity: O(n)

## Radix Sort(Bucket Sort/Bin Sort)
Time complexity: **O(d(n+r~d~))** < O(d(n+r~d~))
Space complexity: O(r~d~)

## External Sort

### Swap-Select Sort

### Best Merge Tree

### Loser Tree

Time complexity: 
1. m个初始归并段进行k路归并，归并趟数**log~k~m(up)**
2. k路归并的败者树高度为**log~2~k(up)+1**，利用败者树从k个记录中选出最值需要进行**log~2~k(up)**次比较，即时间复杂度为**O(log~2~k)**
3. k路归并败者树建树时间复杂度为**O(klog~2~k)**

Space complexity: O(1)

