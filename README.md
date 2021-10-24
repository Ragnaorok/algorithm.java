# algorithm.java
  
    public int[] twoSum(int[] nums, int target) {
         Map<Integer, Integer> numMap = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (numMap.containsKey(complement)) {
                return new int[] { numMap.get(complement), i };
            } else {
                numMap.put(nums[i], i);
            }
        }
        return new int[] {};
    }
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
    public int removeDuplicates(int[] nums) {
        int count = 0;
        for (int i = 1; i < nums.length; i++){
            if(nums[count] != nums[i]){
                nums[++count] = nums[i];
            }
        }
        return count + 1;
    }
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
    public int removeElement(int[] nums, int val) {
        int count = 0;
        for (int i = 0; i < nums.length; i++){
            if (nums[i] != val){
              nums[count] = nums[i];
                count++;
            }
        }
        return count;
    }
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
    public boolean containsDuplicate(int[] nums) {
       Map<Integer, Integer> numMap = new HashMap<>();
       for (int i = 0; i < nums.length; i++){
           int dupe = nums[i];
        if (numMap.containsKey(dupe)){
            
        return true;
       }else{
           numMap.put(nums[i], i);
       }
    }
        return false;
    }
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
      int val;
     TreeNode left;
      TreeNode right;
      TreeNode() {}
      TreeNode(int val) { this.val = val; }
      TreeNode(int val, TreeNode left, TreeNode right) {
          this.val = val;
          this.left = left;
          this.right = right;
          }
      }
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
    public TreeNode invertTree(TreeNode root) {
        if (root == null){
            return root;
        }
        // invert the tree
        TreeNode left = invertTree(root.left);
        TreeNode right = invertTree(root.right);
        
        swap
        root.right = left;
        root.left = right;
        
        return root;
    }
    /////////////////////////////////////////////////////////////////////
    public boolean isValid(String s) {
        HashMap <Character , Character> map = new HashMap <Character, Character> ();
        map.put('(', ')');
        map.put('{', '}');
        map.put('[', ']');
        Stack < Character > stack = new Stack <> ();
        for (int i = 0; i < s.length(); i++) {
            char n = s.charAt(i);
            if (map.keySet().contains(n))
              stack.push(n);
            else if ((map.values().contains(n))){
                if(!stack.isEmpty() && map.get(stack.peek()) == n){
                    stack.pop();
                }else{
                    return false;
                }
            }
        }
        return stack.empty();
    }
     ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
        public boolean isPalindrome(int x) {
        String str = String.valueOf(x);
        String reverse = new StringBuilder(str).reverse().toString();
        return (str.equals(reverse));
    }
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
    public int winCondition(List<int> cards) {
	   int cardsSize = cards.size();
	   Set<int> cardsDupe = new HashSet<>(cards);
	   if (cardsDupe.size() == cardsSize) {
		  int currentMax = cards[0];
		  int currentMaxIndex = 0;
		    for (int i = 0; i < cardsSize; ++i) {
			    int currentCard = cards[i];
			      if (currentCard > currentMax) {
				      currentMax = currentCard;
				      currentMaxIndex = i;
			      }
		    }
		return currentMaxIndex;
	  }
	else if (cardsDupe.size() == 1) {
		return -1;
	}
	return -2;

