Frequency of Elements in an Array in Python
Here, in this page we will discuss the program to count the frequency of elements in an array in python programming language. We are given with an array and need to print each element along its frequency.

Methods Discussed are :
Method 1 : Naive way using extra space.
Method 2 : Naive way without using extra space.
Method 3 : Using Sorting
Method 4 : Using hash Map
Let’s discuss each method one by one,

Method 1 :
In this method we will count the frequency of each elements using two for loops.

To check the status of visited elements create a array of size n.
Run a loop from index 0 to n and check if (visited[i]==1) then skip that element.
Otherwise create a variable count = 1 to keep the count of frequency.
Run a loop from index i+1 to n
Check if(arr[i]==arr[j]), then increment the count by 1 and set visited[j]=1.
After complete iteration of for loop print element along with value of count.
Time and Space Complexity :
Time Complexity : O(n2)
Space Complexity : O(n)
Method 1 : Code in Python
Run
# Python 3 program to count frequencies
# of array items
def countFreq(arr, n):

   # Mark all array elements as not visited
   visited = [False for i in range(n)]

   # Traverse through array elements
   # and count frequencies
   for i in range(n):

     # Skip this element if already
     # processed
     if (visited[i] == True):
        continue

     # Count frequency
     count = 1
     for j in range(i + 1, n, 1):
        if (arr[i] == arr[j]):
          visited[j] = True
          count += 1

     print(arr[i], count)

# Driver Code
arr = [10, 30, 10, 20, 10, 20, 30, 10]
n = len(arr)
countFreq(arr, n)
Output
10 4
30 2
20 2
Related Pages
Sort first half in ascending order and second half in descending

Sort the elements of an array

Sorting elements of an array by frequency

Finding the Longest Palindrome in an Array

Counting Distinct Elements in an Array

Method 2 :
In this method we will use the naive way to find the frequency of elements in the given integer array without using any extra space.

Method 2 : Code in python
Run
# Time Complexity : O(n^2)
# Space Complexity : O(1)

def countFrequency(arr, size):

    for i in range(0, size):
        flag = False
        count = 0

        for j in range(i+1, size):
            if arr[i] == arr[j]:
                flag = True
                break

        # The continue keyword is used to end the current iteration 
        # in a for loop (or a while loop), and continues to the next iteration.
        if flag == True:
            continue

        for j in range(0, i+1):
            if arr[i] == arr[j]:
                count += 1

        print("{0}: {1}".format(arr[i], count))


# Driver Code
arr = [5, 8, 5, 7, 8, 10]
n = len(arr)
countFrequency(arr, n)
Output
5 : 2
7 : 1
8 : 2
10 : 1
Method 3 :
In this method we will sort the array then, count the frequency of the elements.

Time and Space Complexity :
Time Complexity : O(nlogn)
Space Complexity : O(1)
Method 3 : Code in Python
Run
# Time Complexity : O(n log n) + O(n) = O(n logn)
# Space Complexity : O(1)

def countDistinct(arr, n):
    arr.sort()

    # Traverse the sorted array
    i = 0
    while i < n:
        count = 1

        # Move the index ahead whenever
        # you encounter  duplicates
        while i < n - 1 and arr[i] == arr[i + 1]:
            i += 1
            count +=1

        print("{0}: {1}".format(arr[i], count))
        i += 1


# Driver Code
arr = [5, 8, 5, 7, 8, 10]
n = len(arr)
countDistinct(arr, n)
Output
5 : 2
7 : 1
8 : 2
10 : 1
Method 4 :
In this method we will count use hash-map to count the frequency of each elements.

Declare a dictionary dict().
Start iterating over the entire array
If element is present in map, then increase the value of frequency by 1.
Otherwise, insert that element in map.
After complete iteration over array, start traversing map and print the key-value pair.
Time and Space Complexity :
Time Complexity : O(n)
Space Complexity : O(n)
Dictionary in Python
Dictionary in Python is an unordered collection of data values, used to store data values like a map, which, unlike other Data Types that hold only a single value as an element, Dictionary holds key:value pair.
Frequency of element
Method 4 : Code in Python
def countFreq(arr, n):

    mp = dict()

    # Traverse through array elements
    # and count frequencies

    for i in range(n):
        if arr[i] in mp.keys():
            mp[arr[i]] += 1
        else:
            mp[arr[i]] = 1

           
    # Traverse through map and print
    # frequencies

    for x in mp:
        print(x, " ", mp[x])
# Driver Code 

arr = [10, 30, 10, 20, 10, 20, 30, 10] 
n = len(arr) 
countFreq(arr, n)
Output
10 4
20 2
30 2
