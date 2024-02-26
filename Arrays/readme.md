# Arrays and Problems

## Built in functions

```text
1. arrName.length gives the size/length of the array
2. arrname.clone() return the duplicate array

3.asList(T... a): This method returns a fixed-size list backed by the specified array. Changes to the returned list "write through" to the array.

4. binarySearch(T[] a, T key): This method searches the specified array for the specified object using the binary search algorithm. The array must be sorted into ascending order according to the natural ordering of its elements.

5. copyOf(T[] original, int newLength): This method copies the specified array, truncating or padding with zeros (if necessary) so the copy has the specified length.

6. copyOfRange(T[] original, int from, int to): This method copies the specified range of the specified array into a new array. The initial index of the range (from) must lie between zero and original.length, inclusive.

7. deepEquals(Object[] a1, Object[] a2): This method recursively compares the two specified arrays to determine if they are equal to one another.

8. deepHashCode(Object[] a): This method returns a hash code based on the "deep contents" of the specified array.

9. deepToString(Object[] a): This method returns a string representation of the "deep contents" of the specified array.

10. equals(T[] a, T[] a2): This method returns true if the two specified arrays of Objects are equal to one another.

11. fill(T[] a, T val): This method assigns the specified value to each element of the specified array.

12. hashCode(T[] a): This method returns a hash code based on the contents of the specified array.

13. sort(T[] a): This method sorts the specified array into ascending numerical order.

14. toString(T[] a): This method returns a string representation of the contents of the specified array.
```

## Custom functions

1. Print array

```Java
    static void printArr(int[] arr) {
		System.out.println("\nPrinting the array...");
		for (int i = 0; i < arr.length; i++) {
			System.out.print(arr[i] + " ");
		}
	}
```

2. Swap elements of the array

```java
    public void swapInArray(int[] arr, int i, int j) {
		int temp = arr[i];
		arr[i] = arr[j];
		arr[j] = temp;
	}
```

2. Reverse Array elements
```java
    public void reverseInArr(int[] arr) {
		int i = 0, j = arr.length - 1;

		while (i < j) {
			swapInArray(arr, i, j);
			i++;
			j--;
		}
	}
```
- alternative
```java
	public int[] reverseArr(int[] arr) {
		int n = arr.length;
		int[] ans = new int[n];
		int j = 0;
		for (int i = n - 1; i >= 0; i--) {
			ans[j++] = arr[i];
		}

		return ans;
	}
```
3. Reverse the selected range of the array elements
```java
	public void reverse(int arr[], int i, int j) {
		while (i < j) {
			swapInArray(arr, i, j);
			i++;
			j--;
		}
	}
```

4. Rotate the array element according to given input
```java
public void rotateInplace(int arr[], int k) {
	int n = arr.length;
	if (k < 0) {
		return;
	}
	k = k % n;
	reverse(arr, 0, n - k - 1);
	reverse(arr, n - k, n - 1);
	reverse(arr, 0, n - 1);
}
```
- alternative approach
```java
	public int[] rotate(int arr[], int k) {
		int n = arr.length;
		if (k < 0) {
			return arr;
		}
		k = k % n;
		int ans[] = new int[n];

		int j = 0;

		for (int i = n - k; i < n; i++) {
			ans[j] = arr[i];
			j++;
		}
		for (int i = 0; i < n - k; i++) {
			ans[j] = arr[i];
			j++;
		}

		return ans;
	}
```
5. Find the unique element in array

```java 
public int uniqueElement(int arr[]) {
    int n = arr.length;
	int ans = ~n;
	for (int i = 0; i < n; i++) {
		for (int j = i + 1; j < n; j++) {
			if (arr[i] != arr[j]) {
				ans = arr[j];
			}
		}		
    }
	return ans;
}
```
- alternative approach
```java
public int findUnique(int arr[]) {
	int n = arr.length;
	int ans = ~n;

	for (int i = 0; i < n; i++) {
		for (int j = i + 1; j < n; j++) {
			if (arr[i] == arr[j]) {
				arr[i] = -1;
				arr[j] = -1;
			}
		}
	}

	for (int i = 0; i < n; i++) {
		if (arr[i] > 0) {
			ans = arr[i];
		}
	}
	return ans;
}
```
6. Find max element of array
```java
public int findMax(int arr[]) {
	int max = Integer.MIN_VALUE;
	for (int i = 0; i < arr.length; i++) {
		if (arr[i] > max) {
			max = arr[i];
		}
	}
	return max;
}
```
7. find second maximum element in array
``` java
public int findSecondMax(int arr[]) {
	int max = findMax(arr);
	for (int i = 0; i < arr.length; i++) {
		if (arr[i] == max) {
			arr[i] = Integer.MIN_VALUE;
		}
	}
	return findMax(arr);
}
```

8. Find first repeating element of the array
```java
public int findFirstRepeatingElement(int arr[]) {
	int n = arr.length;
	for (int i = 0; i < n; i++) {
		for (int j = i + 1; j < n; j++) {
			if (arr[i] == arr[j]) {
				return arr[j];
			}
		}
	}
	return -1;
}
```

9. Creating a frequency array
``` Java 
	public int[] makeFrequencyArray(int[] arr) {
		int[] freq = new int[100005];
		for (int i = 0; i < arr.length; i++) {
			freq[arr[i]]++;
		}
		return freq;
	}
```

10. sort zeroes and ones using two pointers method
``` Java
public void sortZeroesAndOnesTwoPointers(int[] arr) {
	int left = 0;
	int right = arr.length - 1;
	while (left < right) {
		if (arr[left] == 1 && arr[right] == 0) {
			swapInArray(arr, left, right);
			left++;
			right--;
		}
		if (arr[left] == 0) {
			left++;
		}
		if (arr[right] == 1) {
			right--;
		}
	}
}

```

11. Sort the odd and even values of array using two pointers
```Java 
public void sortOddAndEvenTwoPointers(int[] arr) {
	int left = 0;
	int right = arr.length - 1;
	while (left < right) {
		if (arr[left] % 2 == 1 && arr[right] % 2 == 0) {
			swapInArray(arr, left, right);
			left++;
			right--;
		}
		if (arr[left] % 2 == 0) {
			left++;
		}
		if (arr[right] % 2 == 1) {
			right--;
		}
	}
}
```

12. PairSum or TwoSum
``` Java
public int pairSum(int[] arr, int target) {
	int n = arr.length;
	int ans = 0;
	for (int i = 0; i < n; i++) {
		for (int j = i + 1; j < n; j++) {
			if (arr[i] + arr[j] == target) {
				ans++;
			}
			}
	}
	return ans;
}
```
13. Three sum
``` Java 
public int threeSum(int arr[], int target) {
	int n = arr.length;
	int ans = 0;
	for (int i = 0; i < n; i++) {
		for (int j = i + 1; j < n; j++) {
			for (int k = j + 1; k < n; k++) {
				if ((arr[i] + arr[j] + arr[k]) == target) {
					ans++;
				}
			}
		}
	}
	return ans;
}
```
14. Sort the squares of elements of a non decreasing array.
```java
public int[] sortSquares(int arr[]) {
	int n = arr.length;
	int[] ans = new int[n];
	int left = 0,k=0, right = n - 1;
	while(left<= right) {
		if(Math.abs(arr[left])> Math.abs(arr[right])) {
			ans[k++] = arr[left]* arr[left];
			left++;
		}else {
			ans[k++] = arr[right]*arr[right];
			right--;
		}
	}
	reverseInArr(ans);
	return ans;
}
```