# Window-size-algorithm
You are given an array A. The array contains all the elements in the range of 1 to K. Determine the minimum size of the subarray that contains all the K distinct elements.

def min_window_size(arr, n, k):
    count = {}
    distinct_count = 0
    left = 0
    min_window = float('inf')

    for right in range(n):
        if arr[right] not in count or count[arr[right]] == 0:
            distinct_count += 1
        count[arr[right]] = count.get(arr[right], 0) + 1

        while distinct_count == k:
            min_window = min(min_window, right - left + 1)
            count[arr[left]] -= 1
            if count[arr[left]] == 0:
                distinct_count -= 1
            left += 1

    return min_window if min_window != float('inf') else -1


t = int(input())
for _ in range(t):
    n, k = map(int, input().split())
    arr = list(map(int, input().split()))
    result = min_window_size(arr, n, k)
    print(result)
