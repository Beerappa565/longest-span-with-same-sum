# longest-span-with-same-sum
import java.io.*;
import java.util.*;
class GFG {
    public static int longestspan(int arr1[],int arr2[])
    {
         int n=arr1.length;
        int diff[]=new int[2n+1];//crating an auxiliary array and basically this array used to used store the all differnce values                                        calcuated values
        Arrays.fill(diff,-1);// inititally filling array with -1
       
        int presum1=0;
        int presum2=0;
        int maxlen=0;
        int curr_diff=0;
        int diffindex=-1;
        for (int i=0;i<n;i++)
        {
            presum1+=arr1[i];
            presum2+=arr2[i];
            curr_diff=presum1-presum2;
            diffindex=n+curr_diff;
            if(curr_diff==0)
            {
                maxlen=i+1;
            }
            else if(diff[diffindex]==-1)
            {
                diff[diffindex]=i;
            }
            else
            {
                int len=i-diff[diffindex];
                if(len>maxlen)
                {
                    maxlen=len;
                }
            }
         }
          return maxlen;
    }
    
	public static void main (String[] args) {
		
		int arr1[]={0,0,0,1,0,0};
		int arr2[]={1,1,1,1,1,1};
		
		System.out.println(longestspan(arr1,arr2));
	}
}
