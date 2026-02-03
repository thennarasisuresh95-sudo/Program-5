# Binary Search Tree Operations

class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

def insert(root, data):
    if root is None:
        return Node(data)
    if data < root.data:
        root.left = insert(root.left, data)
    elif data > root.data:
        root.right = insert(root.right, data)
    return root

def search(root, key):
    if root is None:
        return False
    if root.data == key:
        return True
    elif key < root.data:
        return search(root.left, key)
    else:
        return search(root.right, key)

def find_min(root):
    while root.left is not None:
        root = root.left
    return root

def delete(root, key):
    if root is None:
        return root
    if key < root.data:
        root.left = delete(root.left, key)
    elif key > root.data:
        root.right = delete(root.right, key)
    else:
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left
        temp = find_min(root.right)
        root.data = temp.data
        root.right = delete(root.right, temp.data)
    return root

def inorder(root):
    if root:
        inorder(root.left)
        print(root.data, end=" ")
        inorder(root.right)

root = None

while True:
    print("\n--- Binary Search Tree Operations ---")
    print("1. Insert")
    print("2. Search")
    print("3. Delete")
    print("4. Display (Inorder)")
    print("5. Exit")

    choice = int(input("Enter your choice: "))

    if choice == 1:
        val = int(input("Enter value to insert: "))
        root = insert(root, val)
        print("Element inserted.")
    elif choice == 2:
        val = int(input("Enter value to search: "))
        if search(root, val):
            print("Element found in BST.")
        else:
            print("Element not found.")
    elif choice == 3:
        val = int(input("Enter value to delete: "))
        root = delete(root, val)
        print("Element deleted (if present).")
    elif choice == 4:
        print("BST elements (Inorder):")
        inorder(root)
        print()
    elif choice == 5:
        print("Exiting program.")
        break
    else:
        print("Invalid choice.")
output:
--- Binary Search Tree Operations ---
1. Insert
2. Search
3. Delete
4. Display (Inorder)
5. Exit
Enter your choice: 1
Enter value to insert: 50
Element inserted.

Enter your choice: 1
Enter value to insert: 30
Element inserted.

Enter your choice: 1
Enter value to insert: 70
Element inserted.

Enter your choice: 4
BST elements (Inorder):
30 50 70

Enter your choice: 2
Enter value to search: 30
Element found in BST.

Enter your choice: 3
Enter value to delete: 50
Element deleted (if present).
