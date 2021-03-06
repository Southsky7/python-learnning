# 刷题日记

### 1

```python
#给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串 s ，判断字符串是否有效。
有效字符串需满足：
#左括号必须用相同类型的右括号闭合。
#左括号必须以正确的顺序闭合。
def isValid(s):
    if len(s) % 2 == 1:
        return False
    pairs = {
        ']':'[',
        '}':'{',
        ')':'('
    }
    stack = list()
    for elem in s:
        if elem in pairs:
            if not stack or stack[-1] != pairs[elem]:
                return False
            stack.pop()
        else:
            stack.append(elem)
    return not stack
```

### 2

```python
'''用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )'''

'''
思路:队列需要支持队尾插入和队首删除，而栈只能够支持在栈顶插入和删除，所以可以用另一个栈将第一个栈倒序再删除，从而支持删除队尾的操作(从栈顶加入对应从队尾插入)
'''
class CQueue:

    def __init__(self):
        self.A,self.B = [],[]


    def appendTail(self, value: int) -> None:
        self.A.append(value)

    def deleteHead(self) -> int:
        if self.B:
            return self.B.pop()
        if not self.A:
            return -1
        if self.A:
            self.B.append(self.A.pop())
            return self.B.pop()
```

### 3.栈实现队列

```python
'''定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。'''
'''
python中push为append(),pop() 时间复杂度都是o(1),但min()时间复杂度是o(n)，因此此题的难点在于将min()复杂度降为o(1)
思路:使用主栈A和辅助栈B，其中B为非严格降序，因此min只需返回栈B的栈顶元素即可，对于push函数，若push的值小于B的栈顶，则加入，否则直接加入A就好，对于pop函数，若pop的值等于B的栈顶元素，则B也同时pop，否则不变。
'''
class MinStack(object):

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.A,self.B = [],[]

    def push(self, x):
        """
        :type x: int
        :rtype: None
        """
        self.A.append(x)
        if not self.B or self.B[-1] > x:
            self.B.append(x)
    def pop(self):
        """
        :rtype: None
        """
        if self.A.pop() == self.B[-1]:
            self.B.pop()
    def top(self):
        """
        :rtype: int
        """
        return self.A[0]
    def min(self):
        """
        :rtype: int
        """
        return self.B[-1]

```

4.两数求和

```python
'''给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。
你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。
你可以按任意顺序返回答案。
输入：nums = [3,2,4], target = 6
输出：[1,2]
'''
class Solution:
    '''
    做法1:暴力求解   时间复杂度为O(n^2)
    思路:第一循环，从下标为0的数开始，第二循环，下标为1的开始，依次相加，找到target就停止'''
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                if nums[i] + nums[j] == target:
                    return [i,j]
#做法2 哈希表  
#对于值x，寻找哈希表是否存在target-x ，这样寻找target-x的复杂度由O(n)降为O(1)
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        hashtable = dict()   #python里用字典做哈希表，键值对应
        for i,num in enumerate(nums):   #用enumerate同时查找键和下标  查找字典时是在
            if target-num in hashtable:
                return [hashtable[target-num],i]
            hashtable[nums[i]] = i
```

5.输入某年某月某日，判断这一天是这一年的第几天？

```python
import datetime
year = int(input('请输入4位数的年份'))
month = int(input('输入月份'))
day = int(input('输入是几号'))
targetday = datetime.date(year,month,day)
print(targetday-datetime.date(targetday.year-1,12,31))
```

