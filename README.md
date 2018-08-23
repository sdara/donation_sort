10-14-2004
CSC153-02
Project #05

Psuedocode



Using previously available code, make a program that will sort an array of user inputs. Along with this array, there will be two other arrays that will be filled with pointers, and these will be sorted in ascending and descending order.


Make another function (void arrSelectSortDec(int *[], int);) to sort the pointers in DECENDING order.


Add or modify various code for input validation, warnings, and display purposes. Make the output display in three columns.


Source Code

// This program shows the donations made to the United Cause
// by the employees of CK Graphics, Inc. It displays
// the donations in order from lowest to highest
// and in the original order they were received.
#include <iostream.h>
// Function prototypes
void arrSelectSort(int *[], int);
void arrSelectSortDec(int *[], int);
void showArray(int [],int *[],int *[], int);
void showArrPtr(int *[], int);
// numDons is the number of donations
const int numDons = 15;
void main(void)
{
 int *donations; 
 int *arrPtr[numDons];
 int *arrPtr2[numDons];
 int newDonations;
 do
 {
  cout << "Please Enter Number of Donations from 1 to 15: ";
  cin >> newDonations;
  //warning for input validation
  if(newDonations < 1 || newDonations > 15)
		cout << "\n *** Please enter a value from 1 to 15 ***\n\n";
 }while (newDonations < 1 || newDonations > 15);
 donations = new int[newDonations]; // Declare Variable Size Array
 for (int count = 0; count < newDonations; count++)
 {
	 do{
	cout << "Enter Next Donation ("<<count+1<<"): ";
	cin >> donations[count];
	//warning for input validation
	if(donations[count]<0)
		cout << "\n *** Please enter a value greater than 0 ***\n\n";
	 }while(donations[count]<0);
	arrPtr[count] = &donations[count];
  arrPtr2[count] = &donations[count];
 }
 arrSelectSort(arrPtr, newDonations);
 
 arrSelectSortDec(arrPtr2, newDonations);
 
 
 cout << "\nDonation Chart In Ascending, Original, and Descending Order\n================================================================";
 showArray(donations,arrPtr,arrPtr2, newDonations);
cout << "================================================================\n";
cout << "Thank you for using the program.\n\n";
}
 
//****************************************************************
// Definition of function arrSelectSort.                         *
// This function performs an ascending order selection sort on   *
// array, which is an array of pointers. Each element of array   *
// points to an element of a second array. After the sort,       *
// array will point to the elements of the second array in       *
// ascending order.                                              *
//****************************************************************
void arrSelectSort(int *array[], int elms)
{
 int startScan, minIndex;
 int *minElem;
 for (startScan = 0; startScan < (elms - 1); startScan++)
 {
  minIndex = startScan;
  minElem = array[startScan];
  for(int index = startScan + 1; index < elms; index++)
  {
   if (*(array[index]) < *minElem)
   {
    minElem = array[index];
    minIndex = index;
   }
  }
  array[minIndex] = array[startScan];
  array[startScan] = minElem;
 }
}
 
//****************************************************************
// Definition of function arrSelectSortDec.                      *
// This function performs an descending order selection sort on  *
// array, which is an array of pointers. Each element of array   *
// points to an element of a second array. After the sort,       *
// array will point to the elements of the second array in       *
// descending order.                                             *
//****************************************************************
 
void arrSelectSortDec(int *array[], int elms)
{
 int startScan, minIndex;
 int *minElem;
 for (startScan = 0; startScan < (elms - 1); startScan++)
 {
  minIndex = startScan;
  minElem = array[startScan];
  for(int index = startScan + 1; index < elms; index++)
  {
   if (*(array[index]) > *minElem)
   {
    minElem = array[index];
    minIndex = index;
   }
  }
  array[minIndex] = array[startScan];
  array[startScan] = minElem;
 }
}
 
//*************************************************************
// Definition of function showArray.                          *
// This function displays the contents of array. elms is the  *
// number of elements.                                        *
//*************************************************************
void showArray(int array[],int *arrayAsc[], int *arrayDec[], int elms)
{
	cout<<"\n\nAscending\tOriginal\tDescending\n";
	cout<<"=========\t========\t=========\n";
 for (int count = 0; count < elms; count++)
  cout << *(arrayAsc[count]) << "\t\t"<< array[count] << "\t\t"<< *(arrayDec[count])<<endl;
 cout << endl;
}
//**************************************************************
// Definition of function showArrPtr.                          *
// This function displays the contents of the array pointed to *
// by array. elms is the number of elements.                   *
//**************************************************************
void showArrPtr(int *array[], int elms)
{
 for (int count = 0; count < elms; count++)
  cout << *(array[count]) << " ";
 cout << endl;
}
 

Program Output

Please Enter Number of Donations from 1 to 15: 15
Enter Next Donation (1): 100
Enter Next Donation (2): 5
Enter Next Donation (3): 56
Enter Next Donation (4): 99
Enter Next Donation (5): 150
Enter Next Donation (6): 10
Enter Next Donation (7): 1
Enter Next Donation (8): 63
Enter Next Donation (9): 12
Enter Next Donation (10): 5
Enter Next Donation (11): 200
Enter Next Donation (12): 201
Enter Next Donation (13): 77
Enter Next Donation (14): 88
Enter Next Donation (15): 66
 
Donation Chart In Ascending, Original, and Descending Order
================================================================
 
Ascending       Original        Descending
=========       ========        =========
1               100             201
5               5               200
5               56              150
10              99              100
12              150             99
56              10              88
63              1               77
66              63              66
77              12              63
88              5               56
99              200             12
100             201             10
150             77              5
200             88              5
201             66              1
 
================================================================
Thank you for using the program.
 
Press any key to continue



