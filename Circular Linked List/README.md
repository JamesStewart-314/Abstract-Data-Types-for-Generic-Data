# Generic Circular Linked List

[Circular Linked List](https://www.tutorialspoint.com/data_structures_algorithms/circular_linked_list_algorithm.htm) consists of an abstract and linear data structure similar to a standard linked list, with the key distinction that the last node points back to the first node, forming a closed loop. This structure uses a "current" pointer as the reference point for navigating and manipulating elements, which can be traversed both forward and backward continuously without reaching a definitive end.

The most elementary concept used in all circular linked lists corresponds to the "node", a substructure responsible for containing three attributes: The information stored in each element of the list, a pointer to the next node, and a pointer to the previous node, enabling bidirectional traversal.

In the specific implementation of this module, another structure will conventionally be created to encompass all the information necessary to perform the specific operations associated with each single circular linked list instance. Each structure will include:

* A <span style="color:green;">pointer</span> to the currently active element of the circular linked list, denoted by "<span style="color:blue;">currentNode</span>";

* A `size_t` unsigned integer counter that tracks the number of elements currently present in the circular linked list;

* A <span style="color:green;">pointer</span> to an external function whose purpose is to determine the display method of list elements. This parameter is optional; its absence does not prevent the basic functioning of the data structure, but it makes it impossible to display its elements. To do so, simply replace this parameter with a <span style="color:red;">null pointer</span> (<span style="color:red;">NULL</span>) during the instantiation of each circular linked list;

* A **mandatory**, non-null <span style="color:green;">pointer</span> to an external comparison function. This function receives as parameters two <span style="color:green;">pointers</span> to list elements and is designed to perform two-by-two comparisons between elements. The function must return: A **negative** value (less than zero) if the first parameter is considered inferior to the second; **zero** if both given parameters are equal; a **positive** value (greater than zero) if the first parameter is considered superior to the second;

* A <span style="color:green;">pointer</span> to an external function whose purpose is to implement a specific disposal method for each element in the list. This function receives as its only parameter a <span style="color:green;">pointer</span> to the data type stored in the list and performs the release of dynamically allocated memory for the element. If it is not necessary to deallocate memory, this parameter can be replaced with a <span style="color:red;">null pointer</span> (<span style="color:red;">NULL</span>) during the instantiation of each circular linked list;


## Visualization of the structures used in the circular linked list:

```c
typedef struct GENERICCLLISTNODE {
    gCLLPointerData data;
    struct GENERICCLLISTNODE *previous, *next;
} gCLListNode;

typedef struct {
    gCLListNode* currentNode;
    size_t counter;
    impressFunctionGenCLList printF;
    compareFunctionGenCLList compareF;
    destroyFunctionGenCLList destroyF;
} gCLList;
```

## The pre-existing basic operations contained in this module include:
* ***initgCLList*** : Initializes and returns a pointer to the newly initialized circular linked list.
* ***gCLLDestroy*** : Completely destroys the circular linked list, freeing all dynamically allocated memory present in it.
* ***gCLLInsert*** : Inserts a new element after the current node.
* ***gCLLRemoveCurrent*** : Removes the current element; the next element becomes the new current.
* ***gCLLRemove*** : Removes a specific element from the circular linked list.
* ***gCLLClear*** : Removes all elements contained in the circular linked list.
* ***gCLLNext*** : Advances the current pointer to the next element in the list.
* ***gCLLPrevious*** : Moves the current pointer to the previous element in the list.
* ***gCLLImpress*** : Displays on the terminal a visual representation of the elements contained in the circular linked list.
* ***gCLLIsEmpty*** : Informs whether the circular linked list is empty.
* ***gCLLSearch*** : Informs whether a given element is contained in the circular linked list.
* ***gCLLSize*** : Enumerates and informs the number of elements present in the circular linked list.
* ***gCLLGetCurrent*** : Returns the data of the current element of the circular linked list.
* ***gCLLGetBiggest*** : Returns the largest element present in the circular linked list.
* ***gCLLGetSmallest*** : Returns the smallest element present in the circular linked list.


## Usage Instructions
To include this repository locally in your project directory, follow these steps:
1. Open your project folder in the terminal.
2. Type the following command and press enter:
<ul>
    <li><code>git clone https://github.com/JamesStewart314/C-Language-Codes.git</code></li>
</ul>

Now, if everything went as expected, this repository should be present locally on your computer.

Finally, to include the circular linked list functionalities in your project, open your code in an IDE and add, at the top of the file — preferably adjacent to the already existing inclusion directives — the relative path to the header file that contains the prototypes of the circular linked list functions of this module. In the example given above, the specific path to include the header file in the "MainCode.c" code would be:

```c
#include "./Abstract Data Types for Generic Data/Circular Linked List/genCLList.h"
```

Thus, after including the header file in your code with the #include preprocessor directive, the IDE will recognize the functions, which will be available for your respective use.

It is worth mentioning that your project's compilation process must include not only the codes already planned, but also the file containing the implementations of the functions declared in the header file. All these implementations are present in the *genCLList.c* file, so it will be the new file attached to the compilation stage.

Here is an example, in the same context mentioned above, of how to compile the code "MainCode.c" using the GCC compiler, assuming that the Circular Linked List module was included and used in the code:

```c
gcc MainCode.c "./Abstract Data Types for Generic Data/Circular Linked List/genCLList.c" -o ExecutableProgram -I "./Abstract Data Types for Generic Data/Circular Linked List/"
```

<div>
In the above command, we specified the following during the compilation process:

1. Main file: <code>MainCode.c</code> (there may be more than one C file in addition to this, depending on the project context).

2. Relative path to the module: <code>"./Abstract Data Types for Generic Data/Circular Linked List/genCLList.c"</code>, which implements the circular linked list functionalities.

3. Flag for executable name: <code>-o ExecutableProgram</code>, which defines the name of the resulting file after compilation.

4. Flag for the header file directory: <code>-I "./Abstract Data Types for Generic Data/Circular Linked List/"</code>, which indicates the directory containing the header file used.

</div>

For demonstration and clarification purposes, there will be comments adjacent to each function signature, briefly describing its behavior and purpose, contained in the header file (*genCLList.h*). Furthermore, there is also a **commented program** that uses the data structure created in this module, in order to resolve any remaining doubts regarding its use, showing it in practice.
<br></br>

<div align="center">

## Algorithmic Complexity in Big O Notation for the Circular Linked List Operations:

| Operation               | Time Complexity | Space Complexity |
|:-----------------------:|:---------------:|:----------------:|
| Clear                   | O(n)            | O(1)             |
| Destroy                 | O(n)            | O(1)             |
| Get Biggest             | O(n)            | O(1)             |
| Get Current             | O(1)            | O(1)             |
| Get Smallest            | O(n)            | O(1)             |
| Impress                 | O(n)            | O(1)             |
| Insert                  | O(1)            | O(1)             |
| Is Empty                | O(1)            | O(1)             |
| Next                    | O(1)            | O(1)             |
| Previous                | O(1)            | O(1)             |
| Remove                  | O(n)            | O(1)             |
| Remove Current          | O(1)            | O(1)             |
| Search                  | O(n)            | O(1)             |
| Size                    | O(1)            | O(1)             |

</div>
