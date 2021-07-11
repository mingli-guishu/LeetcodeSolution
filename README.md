# LeetcodeSolution
The solutions for Leetcode 
# LeetcodeSolution
The solutions for Leetcode 
    第八课：
        二分模板：
            int left = 0, right = n - 1;
            while (left <= right) {
                int mid = (left + right) / 2;
                if (array[mid] == target)
                    // find the target!
                    break or return mid;
                if (array[mid] < target)
                    left = mid + 1;
                else
                    right = mid - 1;
            }
        lower_bound：第一个>=target的数
            int left = 0, right = n;
            while (left < right) {
                int mid = (left + right) >> 1;
                if (array[mid] >= target) // condition satisfied, should be included
                    right = mid;
                else
                    left = mid + 1;
            }
            return right;
        upper_bound：最后一个<=target的数
            int left = -1, right = n - 1;
            while (left < right) {
                int mid = (left + right + 1) >> 1;
            if (array[mid] <= target) // condition satisfied, should be included
                left = mid;
            else
                right = mid - 1;
            }
            return right;


