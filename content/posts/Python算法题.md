+++
date = '2025-09-23T16:59:01+08:00'
draft = false
title = 'Python algorithm questions'

+++

## 1.我是一名游戏测试，明天我就要面试腾讯的游戏测试工程师岗位，对方有可能会考我的代码能力，让我做算法题，我的主要使用语言是 Python

明天面试的机会很不错！准备一些常见的算法题会对你有帮助。你平时会做哪些类型的算法题呢？比如排序、查找、动态规划、图论这类的，还是有其他专注的领域？如果需要，我可以帮你一起练习。

## 2.我觉得应该就是一些简单或者普通难度的题，你认为我应该准备些什么？

如果是普通难度的题目，可能会涉及一些常见的基础算法和数据结构。你可以重点复习以下几类：

1. **数组与字符串**：
   - 数组的遍历、查找、排序。
   - 字符串的操作（反转、匹配、查找子串）。
   - 示例题目：寻找数组中的最大子数组和、有效的括号匹配、字符串的压缩等。
2. **排序与查找**：
   - 常见的排序算法：快速排序、归并排序、堆排序等，了解它们的时间复杂度。
   - 二分查找相关题目：找出数组中的目标元素、找出第一个和最后一个位置等。
3. **链表**：
   - 链表的基本操作：插入、删除、反转等。
   - 题目示例：合并两个有序链表、判断链表是否有环、链表的中间节点。
4. **栈与队列**：
   - 使用栈和队列来解决问题，如括号匹配、滑动窗口问题等。
   - 示例题目：用栈实现队列、有效的括号问题、滑动窗口最大值。
5. **动态规划**：
   - 常见的动态规划题目：斐波那契数列、背包问题、最大子序和、最小路径和。
   - 理解状态转移方程、子问题的分解。
6. **树与图**：
   - 二叉树的遍历（前序、中序、后序），树的深度和广度优先搜索（DFS/BFS）。
   - 图的遍历、最短路径算法（Dijkstra、Floyd-Warshall 等）。
7. **哈希表**：
   - 用哈希表解决重复问题、计数问题等。
   - 示例题目：两数之和、最长子串、字母异位词。

这些题目都是面试中常见的，可以通过 LeetCode 或者力扣等平台来练习，尽量熟悉一些常见的题型和解法。同时，掌握 Python 的内置函数，比如`collections.Counter`、`heapq`、`itertools`等也能在面试中节省时间，提升解题效率。

你准备得怎么样了？如果有需要，我可以帮你一起复习这些题目。

##

## 3.关于数组和字符串，有什么经典的题可以提供给我的吗，给些示例，带讲解

当然！关于数组和字符串，以下是一些经典的题目以及详细的讲解。通过这些题目，你不仅可以加深对数据结构的理解，还能提升解决实际问题的能力。

### 1. **两数之和 (Two Sum)**

**题目**：给定一个整数数组 `nums` 和一个目标值 `target`，请你在数组中找出两个数，使它们的和等于目标值 `target`，并返回这两个数的索引。

**示例**：

```
makefile复制编辑输入: nums = [2, 7, 11, 15], target = 9
输出: [0, 1]
解释: 因为 nums[0] + nums[1] == 9，所以返回 [0, 1]
```

**解法**： 使用哈希表来优化。我们遍历数组，对于每个元素 `num`，我们检查哈希表中是否存在 `target - num`，如果存在，则说明找到了两个数的和等于目标值。

```
python复制编辑def twoSum(nums, target):
    hashmap = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in hashmap:
            return [hashmap[complement], i]
        hashmap[num] = i
```

**时间复杂度**：O(n)，其中 `n` 是数组的长度。我们只需要遍历一次数组，并且查找哈希表是 O(1) 的操作。

---

### 2. **有效的括号 (Valid Parentheses)**

**题目**：给定一个字符串 `s` 包含只括号字符 `'('`、`')'`、`'{'`、`'}'`、`'['` 和 `']'`，判断字符串是否有效。有效字符串必须满足：

- 左括号必须用相同类型的右括号闭合。
- 左括号必须以正确的顺序闭合。

**示例**：

```
arduino复制编辑输入: s = "()[]{}"
输出: true
arduino复制编辑输入: s = "(]"
输出: false
```

**解法**： 使用栈来辅助匹配。遍历字符串，对于每个左括号，推入栈；对于每个右括号，检查栈顶元素是否为匹配的左括号。

```
python复制编辑def isValid(s):
    stack = []
    mapping = {')': '(', '}': '{', ']': '['}

    for char in s:
        if char in mapping:
            top_element = stack.pop() if stack else '#'
            if mapping[char] != top_element:
                return False
        else:
            stack.append(char)

    return not stack
```

**时间复杂度**：O(n)，其中 `n` 是字符串的长度。我们只遍历一次字符串。

---

### 3. **反转字符串 (Reverse String)**

**题目**：编写一个函数，输入一个字符串，将其反转。

**示例**：

```
arduino复制编辑输入: "hello"
输出: "olleh"
```

**解法**： 可以使用 Python 的切片功能来简单实现字符串反转。

```
python复制编辑def reverseString(s):
    return s[::-1]
```

**时间复杂度**：O(n)，其中 `n` 是字符串的长度。

---

### 4. **最长子串 (Longest Substring Without Repeating Characters)**

**题目**：给定一个字符串 `s`，请你找出其中不含有重复字符的最长子串的长度。

**示例**：

```
makefile复制编辑输入: s = "abcabcbb"
输出: 3
解释: 无重复字符的最长子串是 "abc"，长度为 3。
```

**解法**： 使用滑动窗口技巧。通过维护一个窗口，逐步扩展并更新最长无重复子串的长度。可以用哈希集来记录当前窗口中的字符。

```
python复制编辑def lengthOfLongestSubstring(s):
    char_set = set()
    left = 0
    max_length = 0

    for right in range(len(s)):
        while s[right] in char_set:
            char_set.remove(s[left])
            left += 1
        char_set.add(s[right])
        max_length = max(max_length, right - left + 1)

    return max_length
```

**时间复杂度**：O(n)，其中 `n` 是字符串的长度。每个字符最多被访问两次（一次进入窗口，一次离开窗口）。

---

### 5. **合并区间 (Merge Intervals)**

**题目**：给定一个由若干区间组成的集合，合并所有重叠的区间。

**示例**：

```
lua复制编辑输入: intervals = [[1,3],[2,6],[8,10],[15,18]]
输出: [[1,6],[8,10],[15,18]]
```

**解法**： 首先按照每个区间的起始位置排序，然后遍历区间并合并重叠区间。

```
python复制编辑def merge(intervals):
    if not intervals:
        return []

    intervals.sort(key=lambda x: x[0])
    merged = [intervals[0]]

    for current in intervals[1:]:
        last = merged[-1]
        if current[0] <= last[1]:  # 发现重叠
            last[1] = max(last[1], current[1])  # 合并
        else:
            merged.append(current)

    return merged
```

**时间复杂度**：O(n log n)，因为我们首先对区间进行了排序。

---

这些题目涉及了数组和字符串的常见操作和技巧，掌握这些题目会帮助你应对面试中的大部分基础题目。你可以尝试自己解决一下这些题目，或者如果遇到困难，我可以帮你进一步分析解法。

## 4.关于排序和查找有什么经典例子吗

排序和查找是面试中常见的基础题目，掌握它们的经典解法对于面试非常有帮助。以下是一些常见的排序和查找题目，包含解法和讲解。

### 1. **两数之和 (Two Sum)**

这个问题涉及查找数组中是否存在两个数之和等于目标值，它可以通过排序和二分查找来优化。

**题目**：给定一个数组 `nums` 和目标值 `target`，请你找出数组中两个数的和等于目标值，并返回这两个数的索引。

**示例**：

```
输入: nums = [2, 7, 11, 15], target = 9
输出: [0, 1]
```

**解法**：

- 使用哈希表：可以在 O(n) 的时间内解决问题。
- 使用排序 + 二分查找：可以首先对数组进行排序，之后通过二分查找来找到目标。

```
def twoSum(nums, target):
    nums = [(num, i) for i, num in enumerate(nums)]  # 保留原索引
    nums.sort(key=lambda x: x[0])  # 排序
    left, right = 0, len(nums) - 1

    while left < right:
        current_sum = nums[left][0] + nums[right][0]
        if current_sum == target:
            return [nums[left][1], nums[right][1]]
        elif current_sum < target:
            left += 1
        else:
            right -= 1
```

**时间复杂度**：O(n log n)，因为排序的时间复杂度是 O(n log n)，二分查找的时间复杂度是 O(1)。

---

### 2. **合并两个有序数组 (Merge Sorted Array)**

**题目**：给定两个有序数组 `nums1` 和 `nums2`，将 `nums2` 合并到 `nums1` 中，使得 `nums1` 仍然是有序的。

**示例**：

```
输入: nums1 = [1, 2, 3, 0, 0, 0], m = 3, nums2 = [2, 5, 6], n = 3
输出: [1, 2, 2, 3, 5, 6]
```

**解法**：

- 使用双指针法，从两个数组的末尾开始比较元素，选择较大的放到 `nums1` 的末尾。

```
def merge(nums1, m, nums2, n):
    i, j, k = m - 1, n - 1, m + n - 1
    while i >= 0 and j >= 0:
        if nums1[i] > nums2[j]:
            nums1[k] = nums1[i]
            i -= 1
        else:
            nums1[k] = nums2[j]
            j -= 1
        k -= 1

    while j >= 0:  # 处理 nums2 中剩余的元素
        nums1[k] = nums2[j]
        j -= 1
        k -= 1
```

**时间复杂度**：O(m + n)，遍历两个数组各一次。

---

### 3. **快速排序 (Quick Sort)**

**题目**：给定一个数组，使用快速排序将数组排序。

**示例**：

```
makefile复制编辑输入: nums = [10, 7, 8, 9, 1, 5]
输出: [1, 5, 7, 8, 9, 10]
```

**解法**：

- 快速排序是一种分治算法，选择一个“基准”元素，将数组分成两部分，一部分比基准小，另一部分比基准大，然后对两部分递归排序。

```
python复制编辑def quickSort(nums):
    if len(nums) <= 1:
        return nums
    pivot = nums[0]
    left = [x for x in nums[1:] if x <= pivot]
    right = [x for x in nums[1:] if x > pivot]
    return quickSort(left) + [pivot] + quickSort(right)
```

**时间复杂度**：平均情况 O(n log n)，最坏情况 O(n^2)。

---

### 4. **二分查找 (Binary Search)**

**题目**：在一个已排序的数组中查找目标值。如果找到返回索引，否则返回 -1。

**示例**：

```
makefile复制编辑输入: nums = [-1, 0, 3, 5, 9, 12], target = 9
输出: 4
```

**解法**：

- 二分查找利用数组有序的特点，通过不断折半来快速定位目标。

```
python复制编辑def binarySearch(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

**时间复杂度**：O(log n)，每次查找都减少了一半的区间。

---

### 5. **寻找旋转排序数组中的最小值 (Find Minimum in Rotated Sorted Array)**

**题目**：假设一个升序排序的数组在某个点被旋转，找到旋转数组中的最小值。

**示例**：

```
makefile复制编辑输入: nums = [3, 4, 5, 1, 2]
输出: 1
```

**解法**：

- 旋转数组的最小值总是小于数组的中间元素。我们可以用二分查找来找到最小值。

```
python复制编辑def findMin(nums):
    left, right = 0, len(nums) - 1
    while left < right:
        mid = (left + right) // 2
        if nums[mid] > nums[right]:
            left = mid + 1
        else:
            right = mid
    return nums[left]
```

**时间复杂度**：O(log n)，每次查找都缩小一半的区间。

---

### 6. **寻找第 k 大的元素 (Kth Largest Element in an Array)**

**题目**：给定一个无序的数组，找到其中第 `k` 大的元素。

**示例**：

```
makefile复制编辑输入: nums = [3, 2, 1, 5, 6, 4], k = 2
输出: 5
```

**解法**：

- 可以通过排序来解决，或者使用堆（优先队列）来高效解决。

```
python复制编辑import heapq

def findKthLargest(nums, k):
    return heapq.nlargest(k, nums)[-1]
```

**时间复杂度**：O(n log k)，堆操作的时间复杂度是 O(log k)，共执行 n 次操作。

---

这些题目涵盖了排序和查找的常见技巧和算法，掌握它们不仅有助于解决实际问题，也能在面试中展现出你的算法能力。如果有任何题目不理解或者需要更多的讲解，随时告诉我！

## 5.关于链表，有什么经典的题可以提供给我的吗，给些示例，带讲解

链表是数据结构中常见的题型，很多面试中都涉及到链表的操作。以下是几道经典的链表题目，并附带解法和详细讲解。

### 1. **反转链表 (Reverse Linked List)**

**题目**：给定一个单链表的头节点，反转该链表并返回新的头节点。

**示例**：

```
makefile复制编辑输入: head = [1, 2, 3, 4, 5]
输出: [5, 4, 3, 2, 1]
```

**解法**：

- 使用三个指针来反转链表：`prev`（前一个节点）、`cur`（当前节点）和 `next`（当前节点的下一个节点）。
- 通过逐一改变每个节点的指向来完成链表的反转。

```
python复制编辑class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverseList(head):
    prev = None
    cur = head
    while cur:
        next_node = cur.next  # 保留下一个节点
        cur.next = prev       # 反转当前节点指针
        prev = cur            # 移动 prev 指针
        cur = next_node       # 移动 cur 指针
    return prev
```

**时间复杂度**：O(n)，其中 `n` 是链表的长度。我们遍历链表一次，每个节点的指向改变一次。

---

### 2. **合并两个有序链表 (Merge Two Sorted Lists)**

**题目**：给定两个有序链表 `l1` 和 `l2`，将它们合并为一个新的有序链表并返回。

**示例**：

```
makefile复制编辑输入: l1 = [1, 2, 4], l2 = [1, 3, 4]
输出: [1, 1, 2, 3, 4, 4]
```

**解法**：

- 使用双指针法，分别遍历两个链表，比较当前节点的值，将较小的节点连接到新链表中。
- 继续遍历，直到一个链表遍历完，再将另一个链表的剩余部分连接到新链表。

```
python复制编辑def mergeTwoLists(l1, l2):
    dummy = ListNode(0)  # 哑节点
    current = dummy
    while l1 and l2:
        if l1.val <= l2.val:
            current.next = l1
            l1 = l1.next
        else:
            current.next = l2
            l2 = l2.next
        current = current.next

    # 连接剩余部分
    current.next = l1 if l1 else l2
    return dummy.next
```

**时间复杂度**：O(m + n)，其中 `m` 和 `n` 分别是两个链表的长度。

---

### 3. **删除链表的倒数第 N 个节点 (Remove Nth Node From End of List)**

**题目**：给定一个链表，删除链表的倒数第 N 个节点，返回链表的头节点。

**示例**：

```
makefile复制编辑输入: head = [1, 2, 3, 4, 5], n = 2
输出: [1, 2, 3, 5]
```

**解法**：

- 使用快慢指针法。首先将快指针向前移动 `n` 步，然后快慢指针一起移动，直到快指针到达链表的末尾。此时，慢指针指向的是倒数第 `n` 个节点的前一个节点。

```
python复制编辑def removeNthFromEnd(head, n):
    dummy = ListNode(0)
    dummy.next = head
    fast = slow = dummy

    # 快指针先移动 n 步
    for _ in range(n):
        fast = fast.next

    # 快慢指针一起移动
    while fast.next:
        fast = fast.next
        slow = slow.next

    # 删除节点
    slow.next = slow.next.next
    return dummy.next
```

**时间复杂度**：O(n)，其中 `n` 是链表的长度。我们遍历链表一次。

---

### 4. **链表是否有环 (Linked List Cycle)**

**题目**：给定一个链表，判断链表是否有环。如果链表中有环，返回 `True`，否则返回 `False`。

**示例**：

```
makefile复制编辑输入: head = [3, 2, 0, -4], pos = 1
输出: True  (链表有环，环的起始位置为节点 1)
```

**解法**：

- 使用快慢指针法。如果链表有环，快指针和慢指针一定会在某个时刻相遇。如果没有环，快指针会遍历完链表。

```
python复制编辑def hasCycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:  # 快慢指针相遇
            return True
    return False
```

**时间复杂度**：O(n)，其中 `n` 是链表的长度。快慢指针最多遍历链表一次。

---

### 5. **环的入口节点 (Linked List Cycle Start)**

**题目**：给定一个链表，返回链表中环的起始节点。如果链表无环，返回 `None`。

**示例**：

```
makefile复制编辑输入: head = [3, 2, 0, -4], pos = 1
输出: 2 (环的入口节点是节点 2)
```

**解法**：

- 首先使用快慢指针来检测链表是否有环。如果有环，当快慢指针相遇时，移动慢指针到链表的头部，保持快慢指针的速度不变，两个指针再次相遇的地方就是环的入口。

```
python复制编辑def detectCycle(head):
    slow = fast = head
    # 第一步：检测是否有环
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            # 第二步：找到环的入口
            slow = head
            while slow != fast:
                slow = slow.next
                fast = fast.next
            return slow
    return None
```

**时间复杂度**：O(n)，其中 `n` 是链表的长度。我们通过快慢指针遍历链表两次。

---

### 6. **链表中环的长度 (Linked List Cycle Length)**

**题目**：给定一个链表，返回链表中环的长度。如果链表无环，返回 0。

**解法**：

- 使用快慢指针方法，如果发现有环，相遇后通过移动指针来计算环的长度。

```
python复制编辑def cycleLength(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            # 计算环的长度
            length = 1
            current = slow.next
            while current != slow:
                current = current.next
                length += 1
            return length
    return 0
```

**时间复杂度**：O(n)，其中 `n` 是链表的长度。我们遍历链表至环开始，并且计算环的长度。

---

这些链表的经典题目涉及了从链表的基本操作（反转、合并）到一些较复杂的技巧（快慢指针、环的检测等）。链表在面试中很常见，掌握这些题目不仅能帮助你理解链表的操作，也能帮助你提高在面试中的表现。
