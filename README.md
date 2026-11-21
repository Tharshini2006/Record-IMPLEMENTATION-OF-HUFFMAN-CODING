# IMPLEMENTATION OF HUFFMAN CODING ALGORITHM

**NAME:** THARSHINI.M 
**REG NO:** 212224230287

## Aim

To implement the Huffman Coding algorithm using Python to generate variable-length binary codes for characters based on their frequency of occurrence.

## Software Requirements

- Python
- Anaconda
- Jupyter Notebook

## Huffman Coding

Huffman Coding is a lossless data compression technique used to reduce the size of data. It assigns shorter binary codes to frequently occurring characters and longer binary codes to less frequently occurring characters.

It uses a binary tree to generate unique prefix codes for each character.

## Algorithm

1. Get the input string.
2. Calculate the frequency of each character in the input string.
3. Create tree nodes containing each character and its frequency.
4. Sort the nodes based on their frequencies.
5. Select the two nodes with the smallest frequencies.
6. Combine the two nodes into a new node with their total frequency.
7. Repeat the process until only one node remains.
8. Consider the final node as the Huffman tree.
9. Generate binary codes by traversing the tree.
10. Assign 0 to the left branch and 1 to the right branch.
11. Display each character along with its Huffman code.

## Implementation

### 1. Get the Input String

```python
input_string = "huffman coding"
```

### 2. Calculate Character Frequency

```python
frequency = {}

for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1
```

### 3. Create Tree Nodes

```python
nodes = [[char, freq] for char, freq in frequency.items()]
```

### 4. Build the Huffman Tree

```python
while len(nodes) > 1:

    # Sort nodes based on frequency
    nodes = sorted(nodes, key=lambda x: x[1])

    # Pick two smallest nodes
    left = nodes.pop(0)
    right = nodes.pop(0)

    # Create a new node
    new_node = [[left, right], left[1] + right[1]]

    nodes.append(new_node)

huffman_tree = nodes[0]
```

### 5. Generate Huffman Codes

```python
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code
    else:
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)
```

### 6. Display Huffman Codes

```python
print("Character | Huffman Code")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

## Output

<img width="392" height="360" alt="image" src="https://github.com/user-attachments/assets/59721177-11df-43ce-b5dd-58ce5ca87c4f" />


## Result

Thus, the Huffman Coding algorithm was successfully implemented using Python to generate variable-length binary codes based on the frequency of characters in the input string.
