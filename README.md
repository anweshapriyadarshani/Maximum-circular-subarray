# Maximum-circular-subarray
Given a circular array, compute its maximum subarray sum in O(n) time. A subarray can be empty, and in this case the sum is 0.  For example, given [8, -1, 3, 4], return 15 as we choose the numbers 3, 4, and 8 where the 8 is obtained from wrapping around.  Given [-4, 5, 1, 0], return 6 as we choose the numbers 5 and 1.

#include<bits/stdc++.h>
using namespace std;
//find maximum subarray in sum
int kadane(int a[], int n);
//function returns circular contiguous sum
int maxcircularsum(int a[], int n)
{
	//case 1:maximum sum using kadane's algo
	int maxkadane=kadane(a,n);
	//case 2: maximum elements that imcludes corner elements
	int maxwrap=0, i;
	for(i=0;i<n;i++)
	{
		maxwrap+=a[i];
		a[i]=-a[i];
	}
	//max sum with corner elements
	maxwrap=maxwrap+kadane(a,n);
	//maximum circular will be the sum of two sums
	return(maxwrap>maxkadane)?maxwrap:maxkadane;
}
//kadane algo to find the maximum subarray sum
int kadane(int a[], int n)
{
	int maxsofar=0, maxendinghere=0;
	int i;
	for(i=0;i<n;i++);
	{
		maxendinghere+=a[i];
		if(maxendinghere<0)
			maxendinghere=0;
		if(maxsofar<maxendinghere)
			maxsofar=maxendinghere;
	}
	return maxsofar;
}
//driver code
int main()
{ 
    int a[] = { 11, 10, -20, 5, -3, -5, 8, -13, 10 }; 
    int n = sizeof(a) / sizeof(a[0]); 
    cout << "Maximum circular sum is " << maxCircularSum(a, n) << endl; 
    return 0; 
} 
	


