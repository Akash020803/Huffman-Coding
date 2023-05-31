# Implementation-of-Huffman-Coding-Algorithm
## Aim:
To implement Huffman coding to compress the data using Python.

## Software Required:
1. Anaconda - Python 3.7

## Algorithm:
### Step 1: 
Assign the input string.
### Step 2:
Create the required tree nodes.
### Step 3:
Create a function to implement the huffman coding.
### Step 4:
Calculate frequency of occurence.
### Step 5:
Print the characters and its Huffman code.
## Program:
~~~
Developed by : Akash A
Registration Number : 212221230003
~~~
### Get the input String:
~~~
string = 'Akash 212221230003'
class NodeTree(object):
    def __init__(self,left=None,right=None):
        self.left=left
        self.right=right
    def children(self):
        return (self.left,self.right)
~~~        
### Create tree nodes:
~~~
def huffman_code_tree(node, left=True,binString=''):
        if type(node) is str:
            return {node: binString}
        (l,r) = node.children()
        d= dict()
        d.update(huffman_code_tree(l,True,binString + '0'))
        d.update(huffman_code_tree(r,False,binString + '1'))
        return d
~~~    
### Main function to implement huffman coding:
~~~
fre = {}
for i in string:
    if i in fre:
        fre[i] += 1
    else:
        fre[i] = 1
        
fre = sorted(fre.items(), key=lambda x: x[1],reverse=True)
nodes = fre
~~~
### Calculate frequency of occurrence:
~~~
while len(nodes) >1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree(key1,key2)
    nodes.append((node,c1+c2))
    nodes = sorted(nodes, key=lambda x: x[1],reverse=True)
~~~    
### Print the characters and its huffmancode:
~~~
huffmanCode =huffman_code_tree(nodes[0][0])

print(' Char | Huffman code ')
print('-----------------------------')
for (char,frequency) in fre:
    print(' %-4r |%12s'% (char, huffmanCode[char]))
~~~
## Output:

![out1](https://github.com/Akash020803/Huffman-Coding/assets/94177474/7a709dab-ec22-4199-a09b-0466c8ee92af)


## Result:

Thus, the huffman coding was implemented to compress the data using python programming.
