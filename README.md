# Reverse-pairs-in-arrays
Two numbers in an array. If the first number is greater than the next, the two numbers form an inverse pair. Input an array to find the total number of reverse pairs P in this array. And output the result of P to 100000007. That is, output P% 100000007
public class Solution {
    int count=0;
    public int InversePairs(int [] array) {
        if(array==null||array.length==0) return 0;
        mergesort(array,0,array.length-1);
        return count;
    }
    public void mergesort(int []a,int start,int end){
        if(start>=end) return;
        int mid=(end+start)/2;
        mergesort(a,start,mid);
        mergesort(a,mid+1,end);
        mergeone(a,start,mid,end);
    }
    public void mergeone(int []a,int start,int mid,int end){
        int i=0,p1=start,p2=mid+1;
        int []temp= new int[end-start+1];
        while(p1<=mid&&p2<=end){
            if(a[p1]<=a[p2]){
                temp[i]=a[p1];
                i++;
                p1++;
            }
            else{
                count+=mid-p1+1;
                count%=1000000007;
                temp[i]=a[p2];
                i++;
                p2++;
            }
        }
        while(p1<=mid){
            temp[i]=a[p1];
            i++;
            p1++;
        }
        while(p2<=end){
            temp[i]=a[p2];
            i++;
            p2++;
        }
        for(int j=0;j<temp.length;j++){
            a[start+j]=temp[j];
        }
    }
}
