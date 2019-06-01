#####二维数组中的查找
```python
class Solution:
    def Find(self, target, array):
        # write code here
        ch = len(array[0])
        g = len(array)
        z = g-1
        y = 0
        while z >=0 and y<=ch-1:
            if array[z][y] == target:
                return True
            if array[z][y] > target:
                z -=1
            elif array[z][y] < target:
                y +=1
        return False
```

#####替换空格
```python
class Solution:
    def replaceSpace(self, s):
        # write code here
        ans = ''
        for i in range(len(s)):
            if s[i] != ' ':
                ans +=s[i]
            if s[i] == ' ':
                ans += '%20'
        return ans
```

#####从尾到头打印链表
```python
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None
class Solution:
    def printListFromTailToHead(self, listNode):
        # write code here
        if not listNode:
            return []
        ans = []
        news = listNode
        while news:
            ans.append(news.val)
            news = news.next
        return ans[::-1]
```

#####重建二叉树


#####两个栈实现队列
```python
class Solution:
    s1 = []
    s2 = []
    def push(self, node):
        self.s1.append(node)
    def pop(self):
        ans = self.s1.pop(0)
        while len(self.s1):
            w = self.s1.pop()
            self.s2.append(w)
        while self.s2:
            z = self.s2.pop()
            self.s1.append(z)
        return ans
```

#####旋转数组的最小数字
```
```

#####斐波那契数列
```python
class Solution:
    def Fibonacci(self, n):
        if n == 0:
            return 0
        if n == 1:
            return 1
        f,s,i = 0,1,0
        ans = 0
        while i <n-1:
            ans = f+s
            f = s
            s = ans
            i+=1
        return ans
```

#####跳台阶
```python
class Solution:
    def jumpFloor(self, number):
        # write code here
        if number == 1:
            return 1
        if number == 2:
            return 2
        f,s = 1,2
        ans = 0
        for i in range(3,number+1):
            ans = f+s
            f = s
            s = ans
        return ans
```

#####变态跳台阶
```python
class Solution:
    def jumpFloorII(self, number):
        ans = 1
        for i in range(number-1):
            ans *= 2
        return ans
```

#####矩形覆盖


#####二进制中1的个数
```python
class Solution:
    def NumberOf1(self, n):
        # write code here
        ans = 0
        for i in range(0,32):
            ans += (n >> i) & 1
        return ans
```

#####数值的整数次方
```python
class Solution:
    def Power(self, base, exponent):
        if exponent == 0:
            return 1
        ans = 1
        statue = 1
        if exponent < 0:
            statue = -1
        for i in range(abs(exponent)):
            ans *= base
        if statue == 1:
            return ans
        else:
            return 1/ans
```

#####调整数组顺序
```python
class Solution:
    def reOrderArray(self, array):
        a = []
        b = []
        for i in array:
            if i % 2 == 0:
                a.append(i)
            if i % 2 != 0:
                b.append(i)
        return b + a
```

#####链表倒数第k个节点
```python
class Solution:
    def FindKthToTail(self, head, k):
        # write code here
        ans = []
        ys = head
        while ys != None:
            ans.append(ys)
            ys = ys.next
        if k>len(ys) or k<1:
            return
        else:
            return ans[-k]
```

#####反转链表
```python
class Solution:
    def ReverseList(self, pHead):
        if pHead ==None:
            return pHead
        nt = None
        course = pHead
        while course:
            c = course.next
            course.next = nt
            nt = course
            course = c
        return nt
```

#####合并链表
```python

```

#####二叉树的镜像
```python
class Solution:
    def Mirror(self, root):
        if root == None:
            return root
        root.left,root.right = root.right,root.left
        self.Mirror(root.left)
        self.Mirror(root.right)
        return root
```

#####顺时针打印矩阵
```python
class Solution:
    def printMatrix(self, matrix):
        ans = []
        while matrix:
            ans += matrix.pop(0)
            if matrix and matrix[0]:
                for i in matrix:
                    ans.append(i.pop())
            if matrix:
                ans +=matrix.pop()[::-1]
            if matrix and matrix[0]:
                for i in matrix[::-1]:
                    ans.append(i.pop(0))
        return ans
```

#####二叉树层序遍历
```python
class Solution:
    def PrintFromTopToBottom(self, root):
        if root ==None:
            return []
        dl = [root]
        ans = []
        while dl:
            a = dl.pop(0)
            ans.append(a.val)
            if a.left:
                dl.append(a.left)
            if a.right:
                dl.append(a.right)
        return ans
```

#####数组中次数超过一半的数字
```python
class Solution:
    def MoreThanHalfNum_Solution(self, numbers):
        # write code here
        if not numbers:
            return 
        ans ={}
        for i in numbers:
            if i in ans:
                ans[i] +=1
            else:
                ans[i] = 1
        for i in ans:
            if ans[i] > len(numbers)//2:
                return i
        return 0
```

#####最小K个数
```python
class Solution:
    def GetLeastNumbers_Solution(self, tinput, k):
        if k > len(tinput):
            return []
        ans = self.quick_s(tinput)
        return ans[:k]
    def treal_s(self,list, z, y):
        if z >= y:
            return list
        i = z
        j = y
        switch = list[z]
        while i < j:
            while list[j] >= switch and i < j:
                j -= 1
            while list[i] <= switch and i < j:
                i += 1
            list[i], list[j] = list[j], list[i]
        list[z], list[i] = list[i], list[z]
        self.treal_s(list, z, i - 1)
        self.treal_s(list, j + 1, y)
        return list
    def quick_s(self,list):
        return self.treal_s(list, 0, len(list) - 1)
```

#####连续子数组最大和
```python
class Solution:
    def FindGreatestSumOfSubArray(self, array):
        L= len(array)
        ans = [i for i in array]
        for i in range(1,L):
            ans[i] = max(ans[i-1]+array[i],array[i])
        return max(ans)
```

#####整数中1出现的次数
```python
class Solution:
    def NumberOf1Between1AndN_Solution(self, n):
        ans = 0
        while n>0:
            s = str(n)
            for i in s:
                if i == '1':
                    ans+=1
            n-=1
        return ans
```

#####把数组排成最小的数
```python
class Solution:
    def PrintMinNumber(self, numbers):
        n = len(numbers)
        for i in range(0,n):
            for j in range(i+1,n):
                ans1 = int(str(numbers[i])+str(numbers[j]))
                ans2 = int(str(numbers[j])+str(numbers[i]))
                if ans1>ans2:
                    numbers[i],numbers[j] = numbers[j],numbers[i]
        a = map(lambda x:str(x),numbers)
        return ''.join(a)
```

#####第一个出现一次的字符
```python
class Solution:
    def FirstNotRepeatingChar(self, s):
        ans = {}
        for i in s:
            if i not in ans:
                ans[i] = [s.index(i),0]
            else:
                ans[i] = [s.index(i),1]
        for i in ans:
            if ans[i][1] == 0:
                return ans[i][0]
        return -1
```

#####两个链表第一个公共结点
```python
class Solution:
    def FindFirstCommonNode(self, pHead1, pHead2):
        if pHead2 == None or pHead1 == None:
            return None
        def bs(head):
            ans = []
            while head:
                ans.append(head)
                head = head.next
            return ans
        ans1 = bs(pHead1)
        ans2 = bs(pHead2)
        for i in ans1:
            if i in ans2:
                return i
```

#####

