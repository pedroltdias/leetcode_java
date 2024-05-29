# Solução:

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] array = new int[2];
        for(int i = 0; i < nums.length; i++){
            for(int j = 0; j < nums.length; j++){
                int number1 = nums[i];
                int number2 = nums[j];
                boolean soma = number1 + number2 == target;
                if(soma && i != j){
                    array[0] = i;
                    array[1] = j;
                }
            }
        }
        return array;
    }
}
```


# Refatoração
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        return new int[] {};
    }
}
