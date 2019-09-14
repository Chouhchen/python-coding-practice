# python-coding-practice

Balanced Parenthesis 

“””One can use stack data structure to capture the matching of open parenthesis and close parenthesis. This means when we find a open parenthesis
“””

def balanced_pare(string):
    S = [] # build a stack with list data structure
    count = 0 # counting the number of matching parentheses
    other = []   # if the parenthesis is not matching, I put it into a different list
    for char in string:
        if char == '(':
            S.append(char) # add the open parenthesis to the stack /or the list
        if char == ')':
            if S == []:
                other.append(char)               
            else: 
                S.remove(S[-1]) # remove the open parenthesis because it finds a match
                count +=1 # counting one pair of match
    return count * 2 # there are two parentheses in one matching, so we need to times 2
    
# run the example strings
string1 = "())(())"
string2 = " )(()))))((((()"

print(balanced_pare(string1))
print(balanced_pare(string2))

runfile('/Users/huichenchou/0820.py', wdir='/Users/huichenchou')
6
6

I gave three test cases here to check if the program is fine.
testcase1 = " "
testcase2 = "((("
testcase3 = "((())))"
print(balanced_pare(testcase1))
print(balanced_pare(testcase2))
print(balanced_pare(testcase3))

runfile('/Users/huichenchou/0820.py', wdir='/Users/huichenchou')
0
0
6

 
Histograms and Area

"""Firstly, we can use naive approach for the question, which is to create a list of all the possible rectangle area of the histogram by going through each bar (the y value of the array) along the x axis (  the index of the arry)."""

# create the function to obtain rectangle.

def calc_rects(hisglist):

    for i, cur_h in enumerate(hisglist):
        cur_w = 0
        for old_h in hisglist[i:]:
            if old_h < cur_h:
                cur_h = old_h
        cur_w += 1
        print(i, cur_w, cur_h)

# find the largest rectangle
def largest_rect(hisglist):
    return max(calc_rects(hisglist))

# test case 1
hisglist = [2, 4, 2, 1]
print(largest_rect(hisglist), cur_h)

>> TypeError: 'NoneType' object is not iterable

"""Then one can improve the naive approach with to get the largest rectangle area with divide and conquer by finding the farest length a bar can reach with it’s high ( so the linked bars have to be taller than this bar). """

# Stack data structure is the best to track the maximum area size.

def largest_rect(histl):
    ans = 0
    histl = [-1] + histl
    histl.append(-1)
    n = len(histl)
    stack = [0]  # store index

    for i in range(n):
        while histl[i] < histl[stack[-1]]:
            h = histl[stack.pop()]
            area = h*(i-stack[-1]-1)
            ans = max(ans, area)
        stack.append(i)
    return ans, h

histl = [2, 4, 2, 1]

print(largest_rect(histl))

>> (6, 1)

# the code can not return  the high of the rectangle!!

 
Shortest Word Formed from Car Plates

Code

@author: huichenchou
“””We are given a vocabulary set, but in this exercise, we have no access, so I import an English word dictionary from python library. 
Efficiency can be improved by separate vowels and consonants, so if the number plate letters has consonant only, we can try adding  vowels first.
Search efficiency can also be improved if the vocabulary dataset is constructed with hash function”””

Import itertools 
Import enchant
d = enchant.Dict(word)
letters = [abcdefghijklmnopqrstuvwxyz]

class Car_plate(str):
def __init__(self):
    self.vals = vals

"""read in all the letters and numbers in car plate and extract only letters """  
def read_letters(self, plate):  
    chars = [for ch in plate if ch isalph()]
    chars = ''.joint(chars)
    
"""make set of words out of all the letters of the car plate, 
with permutation function imported from module"""
def make_wordsets(self, chars):
    plate_wordsets = itertools.permutation(chars, len(s))
    return plate_wordsets

"""find shortest word by firstly checking if the letters in car plate can form a word"""
def find_shortest(chars):
    d = enchant.Dict("en_US")
    for word in plate_wordsets:
        if d.check(word)== True:
            return len(word), word
    # if the letters in the plate can not form a word.
    # we add one letter at one time and iterate from all 26 alphabets to find if we can make a word.
    # we can also try suggest() function to come up with the shortest word
        else: 
            for i in range(26):
                    chars = chars.joint(i)
                    plate_wordsets = chars.make_wordsets()
                    for word in plate_wordsets:
                        if d.check(word) == True:
                            return len(word), word
                        else:
                            for j in range(i+1, 26): # if not, we add one more letter and check again
                                chars = chars.joint(letters[j])
                                plate_letters.is_word()
                                return len(word), word
                        return None
                    
p1 = Car_plate(WE1245) 
Print(Car_plate.find_shortest(p1))

Problem
Can not test the code due to "iterator" and "python English dictionary" import failure

 
"""3 Sum Problem:"""

def threeSum(arr, sum):
    for i in range(0, len(arr)-2):
        for j in range (j+1, len(arr)-1):
            for k in range(k+2, len(arr)-2):
                if arr[i]+arr[j]+arr[k] = sum:
                     print(“Match is”, arr[i],”,”, arr[j],”,”,arr[k])
                     return Ture
    # if no match is found
    return False


"""Matrix island problem:"""

def numIslands(self, grid):
    if not grid:
       return 0

    count = 0
    for i in range(len(grid)):
        for j in range(len(grid[0])):
            if grid[i][j] == ‘1’:
                self.dfs(grid, i, j)
                count += 1
    return count  

def defs(self, grid, i, j):
    if i<0, j<0 or i>=len(grid) or j >=len(grid[0]) or grid[i][j] != ‘1’:
    return
    grid[i][j] = ‘#’
    self.dfs(gird, i+1, j)
    self.dfs(gird, i-1, j)    
    self.dfs(gird, i, j+1)
    self.dfs(gird, i, j-1)


Matrix construction:

R = int(input(“Enter the number of rows:”))
C = int(input(“Enter the number of colums:”))

for i in range(R):
    a = []
    for j in range(C):
        a.append(int(input()))
    matrix.append(a)

# printing the matrix
for i in range(R):
    for j in range(C):
        print(matrix[i][j], end = “ “)
    print() 
