# Sorting-Profile
package sorting;

public class BubbleSort {

	static void bubbleSort(int[] arr) {
		int n = arr.length;
		int temp = 0;
		for (int i = 0; i < n; i++) {
			for (int j = 1; j < (n - i); j++) {
				if (arr[j - 1] > arr[j]) {
					// swap elements
					temp = arr[j - 1];
					arr[j - 1] = arr[j];
					arr[j] = temp;
				}

			}
		}

	}

	static void printArray(int arr[]) {
		int n = arr.length;
		System.out.print("sorted array : ");
		for (int i = 0; i < n; i++)
			System.out.print(arr[i] + " ");
	}
}

package sorting;

import java.util.Scanner;

public class Main {

	public static void main(String args[]) {
		int n, choice;
		String ch;
		final String yes="y";
		Scanner input = new Scanner(System.in);
		System.out.println("Welcome to Sorting-Profile ...");
		do {
		System.out.print("\nhow many numbers you want to sort : ");
		n = input.nextInt();
		System.out.print("enter numbers : ");

		int[] arr = new int[n];
		for (int i = 0; i < arr.length; i++) {
			arr[i] = input.nextInt();
		}

		System.out.println("******************************************************");
		System.out.println(
				" 1.Press 1 for Bubble Sort. \n 2.Press 2 for Selection Sort. \n 3.Press 3 for Merge Sort. \n 4.Press 4 for Quick Sort. ");
		System.out.println("******************************************************");
		choice = input.nextInt();
		System.out.println();

		switch (choice) {
		case 1:
			System.out.println("you chose Bubble Sort !");
			BubbleSort.bubbleSort(arr);
			BubbleSort.printArray(arr);
			break;

		case 2:
			System.out.println("you chose Selection Sort !");
			SelectionSort.sort(arr);
			SelectionSort.printArray(arr);
			break;

		case 3:
			System.out.println("you chose Merge Sort !");
			MergeSort.sort(arr, 0, arr.length - 1);
			MergeSort.printArray(arr);
			break;

		case 4:
			System.out.println("you chose Quick Sort !");
			QuickSort.sort(arr, 0, arr.length - 1);
			QuickSort.printArray(arr);
			break;
			
		default:
			System.out.println("you entered wrong choice !");
			break;
		}
		
		System.out.print("\nDo you want to continue y/n : ");
		ch=input.next();
		}while(ch.equals(yes));
		
		System.out.println("\nThank you for using this software ... \n Have a nice day !");

	}

}

package sorting;

public class MergeSort {

	static void merge(int arr[], int l, int m, int r) {

		int n1 = m - l + 1;
		int n2 = r - m;

		int L[] = new int[n1];
		int R[] = new int[n2];

		for (int i = 0; i < n1; ++i)
			L[i] = arr[l + i];
		for (int j = 0; j < n2; ++j)
			R[j] = arr[m + 1 + j];

		int i = 0, j = 0;

		int k = l;
		while (i < n1 && j < n2) {
			if (L[i] <= R[j]) {
				arr[k] = L[i];
				i++;
			} else {
				arr[k] = R[j];
				j++;
			}
			k++;
		}

		while (i < n1) {
			arr[k] = L[i];
			i++;
			k++;
		}

		while (j < n2) {
			arr[k] = R[j];
			j++;
			k++;
		}
	}

	static void sort(int arr[], int l, int r) {
		if (l < r) {

			int m = (l + r) / 2;

			sort(arr, l, m);
			sort(arr, m + 1, r);

			merge(arr, l, m, r);
		}
	}

	static void printArray(int arr[]) {
		int n = arr.length;
		System.out.print("sorted array : ");
		for (int i = 0; i < n; i++)
			System.out.print(arr[i] + " ");
	}

}

package sorting;

public class QuickSort {
	static int partition(int arr[], int low, int high) {
		int pivot = arr[high];
		int i = (low - 1);
		for (int j = low; j < high; j++) {
			if (arr[j] <= pivot) {
				i++;
				int temp = arr[i];
				arr[i] = arr[j];
				arr[j] = temp;
			}
		}

		int temp = arr[i + 1];
		arr[i + 1] = arr[high];
		arr[high] = temp;

		return i + 1;
	}

	static void sort(int arr[], int low, int high) {
		if (low < high) {

			int pi = partition(arr, low, high);

			sort(arr, low, pi - 1);
			sort(arr, pi + 1, high);
		}
	}

	static void printArray(int arr[]) {
		int n = arr.length;
		System.out.print("sorted array : ");
		for (int i = 0; i < n; i++)
			System.out.print(arr[i] + " ");
	}

}


package sorting;

public class SelectionSort {
	static void sort(int arr[]) {
		int n = arr.length;

		for (int i = 0; i < n - 1; i++) {

			int min_idx = i;
			for (int j = i + 1; j < n; j++)
				if (arr[j] < arr[min_idx])
					min_idx = j;

			int temp = arr[min_idx];
			arr[min_idx] = arr[i];
			arr[i] = temp;
		}

	}

	static void printArray(int arr[]) {
		int n = arr.length;
		System.out.print("sorted array : ");
		for (int i = 0; i < n; i++)
			System.out.print(arr[i] + " ");
	}
}
