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
