# third_task

// 1. Find given element in given array (might be unsorted)
#include<iostream>
using namespace std;

int main(){
    int n,l=0,h;
    cin>>n;
    h=n-1;
    int arr[n];
    bool flag;
    for(int i=0; i<n; i++){
        cin>>arr[i];
    }
    int ele;
    cin>>ele;

    for(int i=0; i<n; i++){
        if(arr[i]==ele){
            flag=1;
            break;
        }
    }

    if(flag==1)
        cout<<"The Given Element is present"<<endl;
    else
        cout<<"The Given Element is Not present"<<endl;
        
    return 0;
}


// 2. Find given element in sorted array.

#include <iostream>
using namespace std;
 
int main()
{
    int arr[] = { 2, 3, 4, 10, 40 };
    int ele = 10;
    int l=0;
    int n = sizeof(arr) / sizeof(arr[0]);
    int h = n-1;
    while(l<=h){
        int mid = l + (h - l) / 2;
    
        if (arr[mid] == ele){
            cout << "Element is present";
            return 0;
        }
        if (arr[mid] > ele){
            h = mid - 1;
        }
        else
            l = mid + 1;
    }
    cout << "Element is not present in array";              
    return 0;
}


// 3. Find minimum element in rotated sorted array.

#include <iostream> 
using namespace std; 
    
int main() 
{ 
    int n;
    cin>>n;
    int arr[n];
    for(int i=0; i<n; i++){
        cin>>arr[i];
    }
    int l = 0;
    int h = n-1;
    int last = arr[h];
    while(l<h)
    {
        int mid=l+(h-l)/2;
        if(arr[mid]>last) 
        {
            l=mid+1;
        } 
        else 
        {
            h=mid;
        }
    }
    cout<<arr[l]<<endl;
  return 0; 
} 






// 4. Find given element in rotated sorted array.

#include <iostream> 
using namespace std;

int binSearch(int arr[], int l, int h, int ele){
    if(h<l){
        return -1;
    }

    while(l<=h){
        int mid = l + (h - l) / 2;
    
        if (arr[mid] == ele){
            return mid;
        }
        if (arr[mid] > ele){
            h = mid - 1;
        }
        else
            l = mid + 1;
    }
}

int smallestElementIndex(int arr[], int l, int h){
    int last = arr[h];
    if(h<l){
        return -1;
    }
    while(l<h)
    {
        int mid=l+(h-l)/2;
        if(arr[mid]>last) 
        {
            l=mid+1;
        } 
        else 
        {
            h=mid;
        }
    }
    return l;
}

    
int main() 
{ 
    int n,mid;
    cin>>n;
    int arr[n];
    for(int i=0; i<n; i++){
        cin>>arr[i];
    }
    int ele;
    cin>>ele;
    int l = 0;
    int h = n-1;
    int index = smallestElementIndex(arr, l, h);
    if(index == -1){
        mid=binSearch(arr, l, h, ele);
        if(mid == -1){
            cout<<"The given element is Not present in the given array."<<endl;
        }
        else
        cout<<"The given element is present at the index "<<mid<<" of the given array."<<endl; 
    }
    else if(arr[index] == ele){
        cout<<"The given element is present at the index "<<index<<" of the given array."<<endl;
    }
    else if(arr[index] <= ele)
    {
        mid=binSearch(arr, l, index-1, ele);
        if(mid == -1){
            cout<<"The given element is Not present in the given array."<<endl;
        }
        else
        cout<<"The given element is present at the index "<<mid<<" of the given array."<<endl;
    }
    else{
        mid=binSearch(arr, index+1, h, ele);
        if(mid == -1){
            cout<<"The given element is Not present in the given array."<<endl;
        }
        else
        cout<<"The given element is present at the index "<<mid<<" of the given array."<<endl; 
    }
  return 0; 
} 



// 5. Find given element in sorted array using ternary search

#include<iostream>
using namespace std;

int ternarySearch(int arr[], int l, int h, int ele) {
   if(l <= h) {
      int m1 = (l + (h - l) /3); 
      int m2 = (m1 + (h - l) /3); 
      if(arr[m1] == ele)
         return m1;
      if(arr[m2] == ele)
         return m2;
      if(ele < arr[m1])
         return ternarySearch(arr, l, m1-1, ele);
      if(ele > arr[m2])
         return ternarySearch(arr, m2+1, h, ele);
      return ternarySearch(arr, m1+1, m2-1, ele);
   }
   return -1;
}

int main() {
   int n, ele, index;
   cin >> n;
   int arr[n]; //create an array of size n
   for(int i = 0; i< n; i++) {
      cin >> arr[i];
   }

   cin >> ele;
   if((index = ternarySearch(arr, 0, n, ele)) >= 0)
      cout << "The given element is present at " << index << endl;
   else
      cout << "The given element is not present." << endl;
}

