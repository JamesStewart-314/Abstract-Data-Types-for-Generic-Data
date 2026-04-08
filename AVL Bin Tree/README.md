# Generic AVL Binary Tree

[AVL Binary Tree](https://www.tutorialspoint.com/data_structures_algorithms/avl_tree_algorithm.htm) consists of an abstract and non-linear data structure that corresponds to a self-balancing [Binary Search Tree](https://www.tutorialspoint.com/data_structures_algorithms/binary_search_tree.htm) (BST), named after its inventors Adelson-Velsky and Landis. Its defining property is that the heights of the two child subtrees of any node differ by at most one, automatically performing rotations to maintain this balance invariant after every insertion or deletion. This guarantees **O(log n)** time complexity for all fundamental operations, in contrast to unbalanced BSTs which may degrade to **O(n)** in the worst case.

Each node in the tree stores a data element, a height value used to compute the balance factor, and pointers to its left and right child nodes.

In the specific implementation of this module, another structure will conventionally be created to encompass all the information necessary to perform the specific operations associated with each single AVL Binary Tree instance. Each structure will include:

* A <span style="color:green;">pointer</span> to the root node of the tree, denoted by "<span style="color:blue;">root</span>";

* A `size_t` unsigned integer counter that tracks the total number of elements currently present in the tree;

* A <span style="color:green;">pointer</span> to an external function whose purpose is to determine the display method of tree elements. This parameter is optional; its absence does not prevent the basic functioning of the data structure, but it makes it impossible to display its elements. To do so, simply replace this parameter with a <span style="color:red;">null pointer</span> (<span style="color:red;">NULL</span>) during the instantiation of each AVL Binary Tree;

* A **mandatory**, non-null <span style="color:green;">pointer</span> to an external comparison function. This function receives as parameters two <span style="color:green;">pointers</span> to tree elements and is designed to perform two-by-two comparisons between elements. The function must return: A **negative** value (less than zero) if the first parameter is considered inferior to the second; **zero** if both given parameters are equal; a **positive** value (greater than zero) if the first parameter is considered superior to the second;

* A <span style="color:green;">pointer</span> to an external function whose purpose is to implement a specific disposal method for each element in the tree. This function receives as its only parameter a <span style="color:green;">pointer</span> to the data type stored in the tree and performs the release of dynamically allocated memory for the element. If it is not necessary to deallocate memory, this parameter can be replaced with a <span style="color:red;">null pointer</span> (<span style="color:red;">NULL</span>) during the instantiation of each AVL Binary Tree;

> **⚠️ Dependency Notice:** This data structure depends on both the **Queue** (`genQueue`) and **Stack** (`genStack`) modules, which are located in the same parent directory. The compilation command for any project using this AVL Binary Tree must also include the source files and header paths of these two dependencies.


## Visualization of the structures used in the AVL Binary Tree:

```c
typedef struct GENERICAVLBINTREENODE {
    gAVLBinTrPointerData data;
    size_t height;
    struct GENERICAVLBINTREENODE *left, *right;
} gAVLBinTreeNode;

typedef struct {
    gAVLBinTreeNode* root;
    size_t counter;
    impressFunctionGenAVLBinTree printF;
    compareFunctionGenAVLBinTree compareF;
    destroyFunctionGenAVLBinTree destroyF;
} gAVLBinTree;
```

## The pre-existing basic operations contained in this module include:
* ***initgAVLBinTree*** : Initializes and returns a pointer to the newly initialized AVL Binary Tree.
* ***gAVLBinTreeCopy*** : Creates an identical copy of a given AVL Binary Tree and returns a pointer to the newly created copy.
* ***gAVLBinTreeDestroy*** : Completely destroys the AVL Binary Tree, freeing all dynamically allocated memory present in it.
* ***gAVLBinTreeInsert*** : Inserts a new element into the AVL Binary Tree if it is not already contained there.
* ***gAVLBinTreeRemove*** : Removes a given element from the AVL Binary Tree if it is contained therein.
* ***gAVLBinTreeImpressSymmetric*** : Displays a linear textual representation of the tree through a symmetric (in-order) traversal.
* ***gAVLBinTreeImpressByLevel*** : Displays a linear textual representation of the tree through a level-order traversal.
* ***gAVLBinTreeTextRepr*** : Displays an accurate visual representation of the structure and arrangement of the elements contained in the AVL Binary Tree.
* ***gAVLBinTreeIsEmpty*** : Informs whether the AVL Binary Tree is empty.
* ***gAVLBinTreeIsEquals*** : Determines whether two AVL Binary Trees are identical.
* ***gAVLBinTreeSearch*** : Informs whether a given element is contained in the AVL Binary Tree.
* ***gAVLBinTreeSize*** : Enumerates and informs the total number of elements present in the AVL Binary Tree.
* ***gAVLBinTreeGetNodeHeight*** : Returns the height of a given node in the tree; returns -1 if the element is not found.
* ***gAVLBinTreeGetBiggest*** : Returns a pointer to the largest element contained in the AVL Binary Tree.
* ***gAVLBinTreeGetSmallest*** : Returns a pointer to the smallest element contained in the AVL Binary Tree.


## Usage Instructions
To include this repository locally in your project directory, follow these steps:
1. Open your project folder in the terminal.
2. Type the following command and press enter:
<ul>
    <li><code>git clone https://github.com/JamesStewart314/C-Language-Codes.git</code></li>
</ul>

Now, if everything went as expected, this repository should be present locally on your computer.

Finally, to include the AVL Binary Tree functionalities in your project, open your code in an IDE and add, at the top of the file — preferably adjacent to the already existing inclusion directives — the relative path to the header file that contains the prototypes of the AVL Binary Tree functions of this module. In the example given above, the specific path to include the header file in the "MainCode.c" code would be:

```c
#include "./Abstract Data Types for Generic Data/AVL Bin Tree/genAVLBinTree.h"
```

Thus, after including the header file in your code with the #include preprocessor directive, the IDE will recognize the functions, which will be available for your respective use.

It is worth mentioning that your project's compilation process must include not only the codes already planned, but also the files containing the implementations of the functions declared in the header files. Since this module depends on the Queue and Stack data structures, all of these implementation files must be attached to the compilation stage.

Here is an example, in the same context mentioned above, of how to compile the code "MainCode.c" using the GCC compiler, assuming that the AVL Binary Tree module was included and used in the code:

```c
gcc MainCode.c "./Abstract Data Types for Generic Data/AVL Bin Tree/genAVLBinTree.c" "./Abstract Data Types for Generic Data/Queue/genQueue.c" "./Abstract Data Types for Generic Data/Stack/genStack.c" -o ExecutableProgram -I "./Abstract Data Types for Generic Data/AVL Bin Tree/" -I "./Abstract Data Types for Generic Data/Queue/" -I "./Abstract Data Types for Generic Data/Stack/"
```

<div>
In the above command, we specified the following during the compilation process:

1. Main file: <code>MainCode.c</code> (there may be more than one C file in addition to this, depending on the project context).

2. Relative path to the module: <code>"./Abstract Data Types for Generic Data/AVL Bin Tree/genAVLBinTree.c"</code>, which implements the AVL Binary Tree functionalities, along with its dependencies <code>genQueue.c</code> and <code>genStack.c</code>.

3. Flag for executable name: <code>-o ExecutableProgram</code>, which defines the name of the resulting file after compilation.

4. Flags for the header file directories: <code>-I</code> flags for the AVL Bin Tree, Queue, and Stack directories, which indicate the directories containing the header files used.

</div>

For demonstration and clarification purposes, there will be comments adjacent to each function signature, briefly describing its behavior and purpose, contained in the header file (*genAVLBinTree.h*). Furthermore, there is also a **commented program** that uses the data structure created in this module, in order to resolve any remaining doubts regarding its use, showing it in practice.
<br></br>

<div align="center">

## Algorithmic Complexity in Big O Notation for the AVL Binary Tree Operations:

| Operation               | Time Complexity | Space Complexity |
|:-----------------------:|:---------------:|:----------------:|
| Copy                    | O(n)            | O(n)             |
| Destroy                 | O(n)            | O(1)             |
| Equals                  | O(n)            | O(n)             |
| Get Biggest             | O(log n)        | O(1)             |
| Get Node Height         | O(log n)        | O(1)             |
| Get Smallest            | O(log n)        | O(1)             |
| Impress by Level        | O(n)            | O(n)             |
| Impress Symmetric       | O(n)            | O(n)             |
| Insert                  | O(log n)        | O(log n)         |
| Is Empty                | O(1)            | O(1)             |
| Remove                  | O(log n)        | O(log n)         |
| Search                  | O(log n)        | O(1)             |
| Size                    | O(1)            | O(1)             |
| Text Representation     | O(n)            | O(n)             |

</div>
