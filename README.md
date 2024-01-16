You're given an integer array, where each number exists in pair, but two integers occur once only. i. e. Except for these two integers, the count of all distinct integers is 2.   Find the sum of these two integers that occur once in the array

def find_unique_numbers(arr):
    xor_result = 0

    for num in arr:
        xor_result ^= num

    rightmost_set_bit = xor_result & -xor_result

    group1_xor = 0
    group2_xor = 0

    for num in arr:
        if num & rightmost_set_bit:
            group1_xor ^= num
        else:
            group2_xor ^= num

    return group1_xor + group2_xor

n = int(input())

arr = list(map(int, input().split()))

result = find_unique_numbers(arr)
print(result)
