# Coding-challenge-Questions
Q1. Finding duplicates

int findDuplicate(int* nums, int numsSize){
    int result;
    for(int i=0; i<numsSize; i++){
        for(int j=i+1; j<numsSize; j++){
            if(*(nums+i) == *(nums+j)){
                result= *(nums+i);
            }
        }
    }
    return result ;
}

Q2.Sorting Colors

void sortColors(int* nums, int numsSize){
    int temp;
    for(int i=0; i<numsSize; i++){
        for(int j=i+1; j<numsSize; j++){
            if((nums+i)>(nums+j)){
                temp=*(nums+i);
                (nums+i)=(nums+j);
                *(nums+j)=temp;
                
            }
        }
    }
    return temp;

}

Q3. Remove Dulicates

int removeDuplicates(int* nums, int numsSize){
   if( nums == NULL || numsSize<2){
       return numsSize;
   }
    
    int j=0;
    for(int i=1; i<numsSize; i++){
        if(nums[i]!=nums[j]){
            j++;
            nums[j]=nums[i];
        }
    }
    return 1+j;
        
   
}

Q4. Set matrix Zeroes

class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int m=matrix.size();
        int n=matrix[0].size();
        int row[m], col[n];
        
        for(int i=0; i<m;i++){
            row[i]=1;
        }
        for(int i=0; i<n; i++){
            col[i]=1;
        }
        for(int i=0; i<m ;i++){
            for(int j=0; j<n; j++){
                if(matrix[i][j]==0){
                    row[i]=0;
                    col[j]=0;
                }
            }
        }
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(row[i]==0 || col[j]==0){
                    matrix[i][j]=0;
                }
            }
        }
        
    }
       
        
        
       
}
    Q5.Move Zeroes
    
    class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int n=nums.size();
        vector<int> temp;

        for(int i=0; i<n; i++){
            if(nums[i]==0){
                temp.push_back(i);
            }
        }
        int i=temp.size()-1;
        while(i > -1)
        {
            nums.erase(nums.begin()+temp[i]); 
			nums.push_back(0);
            i--;
        }
    }
};
    Q6. Best time to buy and sell stock
    
    int maxProfit(int* prices, int pricesSize){
       int maxp=0;
       int min=prices[0];
       for(int i=1; i<pricesSize; i++){
           if(prices[i]-min>maxp){
               maxp=prices[i]-min;
           }
           if(prices[i]<min){
               min=prices[i];
           }
       }
     return maxp;
}
Q7.two sum

   class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> sum;
        for(int i=0;i<=nums.size();i++){
         for(int j=i+1;j<nums.size();j++){
             if(nums[i]+nums[j]==target){
                  sum.push_back(i);
                  sum.push_back(j);
         }
         }
     }
  return sum;
    }
};
   Q8. return max profit in buy and sell problem
    
    class Solution {
public:
    int maxProfit(vector<int>& prices) {
       int maxp=0;
        int total=0;
        int n=prices.size();
       for(int i=0; i<n-1; i++){
          maxp=prices[i+1]-prices[i];
           if(maxp<0){
               maxp=0;
           }
           
           if(maxp>0){
            total=total+maxp;
           }
       }
     return total;

    }
};
    Q9. Finding all dulicates
    class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        int n=nums.size();
        int i,j;
        vector<int> temp;
        for( i=0; i<n; i++){
            for(j=i+1; j<n; j++){
                if(nums[i]==nums[j]){
                    temp.push_back(nums[i]);
                }
            }
        }
        sort(temp.begin(),temp.end());
        return temp;
    }
};
 Q10.*** Three Sum
    
    class Solution {
public:
vector<vector> threeSum(vector& nums) {
int n = nums.size();
if(n < 3) return {};
vector<vector> ans;
sort(nums.begin(), nums.end());
int j, k , sum;
for(int i = 0; i < n - 2; i++) {
if( i == 0 || nums[i] != nums[i - 1]) {
j = i + 1;
k = n - 1;
while(j < k)
{
sum = nums[i] + nums[j] + nums[k];
if(sum == 0)
{
ans.push_back({nums[i], nums[j], nums[k]});
while(j < k && nums[j] == nums[j + 1]) j++;
while(j < k && nums[k] == nums[k - 1]) k--;
j++; k--;
}
else if(sum > 0) k--;
else j++;
}
}
} return ans;
}
};

	
// String 
Q1. Check Valid parenthesis
	
class Solution {
public:
    bool isValid(string s) {
        stack<char> p;
        for(int i=0; i<s.size(); i++){
            char c=s[i];
            if(c=='(' || c=='['|| c=='{'){
                p.push(c);
            }
            else {
                if(!p.empty()){
                 char top= p.top();
                    if(c==']' && top=='['||
                       c==')'&& top=='('|| 
                       c=='}'&& top=='{'){
                        p.pop();
                    }
                    else{
                        return false;
                    }
                }
                else{
                    return false;
                }
            }
            
        }
        if(p.empty()){
            return true;
        }
        else{
           return false;
        }
    }
        
};

Q2. Finding substring in given string 
				 
class Solution {
public:
    int strStr(string haystack, string needle) {
        if(needle.length()==0){
            return 0;
        }
       int x=haystack.find(needle);
           if(x !=-1){
               return x;
           }
           else{
               return -1;
           }
        
    }
};
				 
Q3. Longest Prefix
	
 class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.size()==1){
            return strs[0];
        }
        string s=strs[0];
        int i=0;
        while(true){
            for(int j=1; j<strs.size(); j++){
                if(strs[j].size()==i || strs[j][i]!=s[i]){
                    return s.substr(0,i);
                }
            }
            i++;
        }
        
        return "";
    }
};

Q4.Integer to roman

class Solution {
public:
 
    string intToRoman(int num) {
        int val[] = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
 string roman[]={"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
        string p="";
        int i=0;
        while(num){
            
            while(num>=val[i]){
                p+=roman[i];
                num-=val[i];
            }
            i++;
        }
         return p; 
    }
    
};
