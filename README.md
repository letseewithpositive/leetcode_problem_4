# leetcode_problem_4
Solution of leetcode problem 4
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int n=nums1.size(),m=nums2.size();
        if(m<n)
            return findMedianSortedArrays(nums2,nums1);
        int l=0,r=n;
        while(l<=r){
            int mid=(l+r)/2;
            int n1=mid;
            int n2=(n+m+1)/2-n1;
            double start1= n1>0? nums1[n1-1]: INT_MIN;
            double start2= n2>0 ? nums2[n2-1]:INT_MIN;
            double end1= n1<n? nums1[n1]: INT_MAX;
            double end2= n2<m? nums2[n2]: INT_MAX;
            if(start1<=end2&&start2<=end1){
                if((n+m)%2==0)
                    return (max(start1,start2)+min(end1,end2))/2.0;
                else return max(start1,start2);
            }
            else if(start1>end2)
                r=mid-1;
            else l=mid+1;
        }
        return 0.0;
    }
};
