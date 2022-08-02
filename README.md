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

//Mathematical problem

Q1.minimum moves to make all elements of array are equal
	
class Solution {
public:
    int minMoves(vector<int>& nums) {
        int n=nums.size();
        sort(nums.begin(), nums.end());
        int x=nums[0];
        int count=0;
        for( int i=0; i<n; i++){
              count+=nums[i]-x;
     }
        return count;
        
    }
};

Q2.Add two binary strings		
			   
class Solution {
public:
    string addBinary(string a, string b) {
        int n1=a.size();
        int n2=b.size();
        int carry=0;
        int i=0;
        string ans="";
        while(i<n1 || i<n2 || carry!=0){
            int x=0;
            if(i<n1 && a[n1-i-1]=='1'){
                x=1;
            }
            int y=0;
            if(i<n2 && b[n2-i-1]=='1'){
                y=1;
            }
            ans=to_string((x+y+carry)%2)+ ans;
            carry=(x+y+carry)/2;
            i=i+1;
        }
        
        return ans;
    }
};
		    
Q3.Find Maximum product of three number.

class Solution {
public:
    int maximumProduct(vector<int>& nums) {
        int n=nums.size();
        sort(nums.begin(),nums.end());
        long long x,y,z;
        x=nums[n-1]*nums[n-2]*nums[n-3];
        y=nums[n-1]*nums[0]*nums[1];
        z=nums[0]*nums[1]*nums[2];
        return max(x,max(y,z));
    }
};

Q4.//input
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
...

class Solution {
public:
    string convertToTitle(int columnNumber) {
        string ans="";
        int rem;
        while(columnNumber){
            columnNumber--;
            rem=columnNumber%26;
            char c='A'+rem;
            ans=c+ans;
            columnNumber/=26;
        }
        return ans;
       }
};	
	
Q5.Input:
n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
	
class Solution {
public:
       bool isHappy(int n){
           if(n==1){
               return true;
           }
           if(n==2 || n==3 || n==4|| n==5|| n==6|| n==8|| n==9){
               return false;
           }
           if(n==7){
               return true;
           }
           int sum=0;
           int r;
           while(n!=0){
                r=n%10;
                sum+=r*r;
                n=n/10;
           }
           if(sum==1){
               return true;
           }
           else{
               return isHappy(sum);
           }
           
}
};
	
Q6.Palindrome number

class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0){
            return false;
        }
         int n=x;
         long long int s=0;
        while(x!=0){
            int r=x%10;
            s=(long long int)(s * 10)+r;
            x/=10;
         }
        
        if(s==n){
            return true;
       }
        else{
            return false;
        }
    }
};

Q7.Find Missing Number
		 
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n=nums.size();
        int x;
        sort(nums.begin(),nums.end());
        for(int i=0; i<n; i++){
           if(nums[i]!=i){
                return i;
            }
           
        }
        return n;
    }
};

Q8.Find Reverse of given Digit with given constraints.

class Solution {
public:
    int reverse(int x) {
        long long int rev=0;
        
        while(x!=0){
            int r=x%10;
            rev=(long long int)(rev*10)+r;
            x=x/10;
        }
//following is the constraints
        if(rev>INT_MAX || rev<INT_MIN){
            return 0;
}
        return rev;
    }
};
					
Q8. Find Power of Two.
					
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if(n==1){
            return true;
        }
        if(n<1){
            return false;
        }
        while(n>=2){
            if(n%2!=0){
                return false;
            }
            n=n/2;
        }
         return true; 
    }
	
Q9.Input: n = 12, k = 3
Output: 3
Explanation: Factors list is [1, 2, 3, 4, 6, 12], the 3rd factor is 3.
	
class Solution {
public:
    int kthFactor(int n, int k) {
        vector<int> temp;
        
        for(int i=1; i<=n; i++){
            if(n%i==0){
                temp.push_back(i);
            }
            
        }
        if(temp.size()<k){
            return -1;
        }
       else{
        return temp[k-1];
       }
    }
};	

	
//Linked List	

Q1.Find Midddle of linked list
	
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        int x=0;
        ListNode* temp=head;
        while(temp!=NULL){
            x++;
            temp=temp->next;
        }
        temp=head;
        for(int i=0; i<x/2; i++){
            temp=temp->next;
        }
       return temp;
    }
};
	
Q2.Find if cycle present in linked list or not.
	
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if(head==NULL){
            return false;
        }
        ListNode* slow=head;
        ListNode* fast=head;
        while(fast!=NULL && fast->next!=NULL){
            fast=fast->next->next;
            slow=slow->next;
            if(fast==slow){
                return true;
            }
        }
        return false;
    }
};
	
Q3.Remove Duplicates From sorted list
	
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode* temp=head;
        if(head==NULL){
            return head;
        }
       
        while(temp->next!=NULL){
            if(temp->val==temp->next->val){
                temp->next=temp->next->next;
            }
            else{
                temp=temp->next;
            }
        }
        return head;
        
    }
};	

Q4. Convert Binary number in linked list to integer.

class Solution {
public:
    int getDecimalValue(ListNode* head) {
        
        ListNode* temp=head;
        int n=0;
        while(temp->next!=NULL){
            n++;
            temp=temp->next;
            
        }
        temp=head;
        int dec=0;
        while(temp!=NULL){
            dec=dec+temp->val*pow(2,n);
            n--;
            temp=temp->next;
        }
        return dec;
    }
};

Q5.Remove linked list element.

class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode* temp=head;
        ListNode* prev;
        if(head==NULL){
            return head;
        }
        while(temp!=NULL){
             
            if(temp->val==val){
                if(temp==head){
                    head=temp->next;
                }
                else{
                    prev->next=temp->next;
                    temp=temp->next;
                }
                 
           }
            else{
                prev=temp;
                temp=temp->next;
            }
        }
        return head;
    }
};

Q6.Merge Two sorted linked list.

// Recursive approach
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* result;
        if(list1==NULL){
            return list2;
        }
        if(list2==NULL){
            return list1;
        }
        if(list1->val < list2->val){
            result=list1;
            result->next=mergeTwoLists(list1->next, list2);
        }
        else{
            result=list2;
            result->next=mergeTwoLists(list1, list2->next);
        }
        return result;
    }
};

//Iterative approach

node *merge(node* list1,node* list2){
node* p1=list1;
node* p2=list2;
node* list3=new node(-1);
node* p3=list3;

while(p1!=NULL && p2!=NULL){
if(p1->val < p2->val){
p3->next=p1;
p1=p1->next;
}
else{
p3->next=p2;
p2=p2->next;
}
p3=p3->next;
}
while(p1!=NULL){
p3->next=p1;
p1=p1->next;
p3=p3->next;
}
while(p2!=NULL){
p3-.next=p2;
p2=p2->next;
p3=p3->next;
}
return list3->next;
}

Q7.Reverse Linked list

class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev=NULL;
        ListNode* curr=head;
        ListNode* nextp;
        while(curr!=NULL){
            nextp=curr->next;
            curr->next=prev;
            
            prev=curr;
            curr=nextp;
        }
        return prev;
    }
};

Q8.Palindrome linked list.

class Solution {
public:
    ListNode* reverse(ListNode* head){
        ListNode* prev=NULL;
        ListNode* curr=head;
        ListNode* nextp;
        while(curr!=NULL){
            nextp=curr->next;
            curr->next=prev;
            prev=curr;
            curr=nextp;
        }
        return prev;
    }
    bool isPalindrome(ListNode* head) {
        if(head==NULL || head->next==NULL){
            return true;
        }
        ListNode* slow=head;
        ListNode* fast=head;
        while(fast->next!=NULL && fast->next->next!=NULL ){
            slow=slow->next;
            fast=fast->next->next;
        }
        slow->next=reverse(slow->next);
        slow=slow->next;
        while(slow != NULL)
        {
            if(head->val != slow->val)
            {
                return false;
            }
            head = head->next;
           slow = slow->next;
        }
      return true;
  
    }
};

Q9. Sort list.

 class Solution {
public:
    ListNode* sortList(ListNode* head) {
         if(head==NULL || head->next==NULL){
             return head;
         }
        ListNode* temp=NULL;
        ListNode* slow=head;
        ListNode* fast= head;
        while(fast!=NULL && fast->next!=NULL){
            temp=slow;
            slow=slow->next;
            fast=fast->next->next;
        }
        temp->next=NULL;
        
        ListNode* l1=sortList(head);
        ListNode* l2=sortList(slow);
        
        return mergeList(l1,l2);
        
    }
    ListNode* mergeList(ListNode* l1, ListNode* l2){
         ListNode* p1=l1;
         ListNode* p2=l2;
         ListNode* l3=new  ListNode(0);
         ListNode* p3=l3;
        while(p1!=NULL && p2!=NULL){
            if(p1->val < p2->val){
                p3->next=p1;
                p1=p1->next;
            }
            else{
                p3->next=p2;
                p2=p2->next;
            }
            p3=p3->next;
        }
    
    while(p1!=NULL){
        p3->next=p1;
        p1=p1->next;
        p3=p3->next;
    }
     while(p2!=NULL){
        p3->next=p2;
        p2=p2->next;
        p3=p3->next;
    }
    return l3->next;
    }
}; 

Q10. Add two numbers.

class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* l3= new ListNode(0);
        ListNode* p=l3;
        long sum=0, carry=0;
        while(l1!=NULL || l2!=NULL || carry!=0){
            sum=0;
            if(l1!=NULL){
                sum=sum+l1->val;
                l1=l1->next;
            }
            if(l2!=NULL){
                sum=sum+l2->val;
                l2=l2->next;
            }
            sum=sum+carry;
            int a=sum%10;
            ListNode* n=new ListNode(a);
            p->next=n;
            p=n;
            carry=sum/10;
        }
        return l3->next;
        
    }
};

Q.Three Sum....
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
          int n = nums.size();
        vector<vector<int>> ans;
        sort(nums.begin(), nums.end());
        for(int i=0; i<n; i++)
        {
            int tar = -nums[i];
            
            int a=i+1, b=n-1;
            while(a<b)
            {
                int x = nums[a];
                int y = nums[b];
                if(x+y<tar)
                    a++;
                else if(x+y>tar)
                    b--;
                else
                {
                    ans.push_back({x, y, nums[i]});
                    while(a<i && nums[a]==x)
                        a++;
                    while(b>i && nums[b]==y)
                        b--;
                }
            }
            while(i<n-1 && nums[i+1]==nums[i])
                i++;
        }
        return ans;
    }
};

Q.Three Sum closest..

class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        int n=nums.size();
        sort(nums.begin(),nums.end());
        int closest=nums[0]+nums[1]+nums[2];
        for(int i=0; i<n; i++){
          
            
            int a=i+1, b=n-1;
            while(a<b)
            {
                int sum=nums[i]+nums[a]+nums[b];
                if(abs(target-sum)<abs(target-closest)){
                    closest=sum;
                }
               if(sum<target){
                    a++;
                }
                else if(sum > target){
                    b--;
                }
                else{
                    return sum;
                }
            }   

        }
        return closest;
	}
	};

//graph

Q.Flood fill

class Solution {
public:
    
    void dfs(int i,int j,int initialColor, int color,vector<vector<int>>& image){
        int n=image.size();
        int m=image[0].size();
        if(i<0 || j<0) return;
        if(i>=n || j>=m) return;
        if(image[i][j]!=initialColor) return;
        
        image[i][j]=color;
        
        dfs(i-1,j,initialColor,color,image);
        dfs(i+1,j,initialColor,color,image);
        dfs(i,j-1,initialColor,color,image);
        dfs(i,j+1,initialColor,color,image);
    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        int initialColor=image[sr][sc];
        if(initialColor!=color){
            dfs(sr,sc,initialColor,color,image);
        }
        return image;
    }
};
