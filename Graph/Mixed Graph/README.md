# Generic Mixed Graph

[Graph](https://www.tutorialspoint.com/data_structures_algorithms/graph_data_structure.htm) consists of an abstract and non-linear data structure composed of a finite set of **vertices** (or nodes) and **edges** (or arcs) connecting pairs of vertices. This specific implementation is a **Mixed Graph**, meaning it supports both **bidirectional** (undirected) edges and **unidirectional** (directed) edges simultaneously within the same graph structure.

Each vertex stores a data element and maintains an adjacency list — implemented as a Linked List — of its neighboring vertices. The graph uses a linked chain of vertices to traverse and manage all vertices in the structure.

In the specific implementation of this module, another structure will conventionally be created to encompass all the information necessary to perform the specific operations associated with each single mixed graph instance. Each structure will include:

* A <span style="color:green;">pointer</span> to the currently active (head) vertex of the graph, denoted by "<span style="color:blue;">currentVertex</span>";

* A 32-bit unsigned integer counter, which can represent values contained in the interval **0** to **4,294,967,295**, where the limits of this interval are inclusive;

* A <span style="color:green;">pointer</span> to an external function whose purpose is to determine the display method of graph elements. This parameter is optional; its absence does not prevent the basic functioning of the data structure, but it makes it impossible to display its elements. To do so, simply replace this parameter with a <span style="color:red;">null pointer</span> (<span style="color:red;">NULL</span>) during the instantiation of each mixed graph;

* A **mandatory**, non-null <span style="color:green;">pointer</span> to an external comparison function. This function receives as parameters two <span style="color:green;">pointers</span> to graph elements and is designed to perform two-by-two comparisons between elements. The function must return: A **negative** value (less than zero) if the first parameter is considered inferior to the second; **zero** if both given parameters are equal; a **positive** value (greater than zero) if the first parameter is considered superior to the second;

* A <span style="color:green;">pointer</span> to an external function whose purpose is to implement a specific disposal method for each element in the graph. This function receives as its only parameter a <span style="color:green;">pointer</span> to the data type stored in the graph and performs the release of dynamically allocated memory for the element. If it is not necessary to deallocate memory, this parameter can be replaced with a <span style="color:red;">null pointer</span> (<span style="color:red;">NULL</span>) during the instantiation of each mixed graph;

* A <span style="color:green;">pointer</span> to an external function whose purpose is to produce completely independent replicas of each element contained in the graph, that is, the function will perform a [deep copy](https://developer.mozilla.org/en-US/docs/Glossary/Deep_copy). The function's only parameter is a <span style="color:green;">pointer</span> to the element to be copied, and it will return a <span style="color:green;">pointer</span> to the new copied element. It's only necessary if the structure of the elements stored in the graph involves dynamic memory allocation, otherwise, the copy function parameter may be replaced with a <span style="color:red;">null pointer</span> (<span style="color:red;">NULL</span>).

> **⚠️ Dependency Notice:** This data structure depends on the **Linked List** (`genLinkedList`) module, which is located in the same parent directory. The compilation command for any project using this Mixed Graph must also include the source file and header path of this dependency.


## Visualization of the structures used in the mixed graph:

```c
typedef struct GENERICMIXEDGRAPHVERTEX {
    gMiexdGraphDataPtr data;
    gLinkedList* neighboringVertices;
    struct GENERICMIXEDGRAPHVERTEX* nextVertex;
} gMixedGraphVertex;

typedef struct GENERICMIXEDGRAPH {
    gMixedGraphVertex* currentVertex;
    uint32_t counter;
    impressFunctionGenMixedGraph printF;
    compareFunctionGenMixedGraph compareF;
    destroyFunctionGenMixedGraph destroyF;
    deepcopyFunctionGenLinkedList deepcopyF;
} gMixedGraph;
```

## The pre-existing basic operations contained in this module include:
* ***initgMixedGraph*** : Initializes and returns a pointer to the newly initialized mixed graph.
* ***gMixedGraphCopy*** : Creates a copy of a given mixed graph and returns a pointer to the new copy.
* ***gMixedGraphClear*** : Removes all vertices and edges contained in the mixed graph.
* ***gMixedGraphDestroy*** : Completely destroys the mixed graph, freeing all dynamically allocated memory present in it.
* ***gMixedGraphImpress*** : Displays on the terminal a visual representation of all vertices and their adjacency lists.
* ***gMixedGraphInsertVertex*** : Inserts a new vertex into the mixed graph.
* ***gMixedGraphRemoveVertex*** : Removes a specific vertex and all its associated edges from the mixed graph.
* ***gMixedGraphCreateEdge*** : Creates a bidirectional (undirected) edge between two vertices.
* ***gMixedGraphRemoveEdge*** : Removes the bidirectional edge between two vertices.
* ***gMixedGraphCreateUnidirectionalEdge*** : Creates a unidirectional (directed) edge from a source vertex to a destination vertex.
* ***gMixedGraphRemoveUnidirectionalEdge*** : Removes the unidirectional edge from a source vertex to a destination vertex.
* ***gMixedGraphIsEmpty*** : Informs whether the mixed graph contains no vertices.
* ***gMixedGraphIsEquals*** : Determines whether two mixed graphs are identical in structure and content.
* ***gMixedGraphSearchVertex*** : Informs whether a given vertex is contained in the mixed graph.
* ***gMixedGraphSearchEdge*** : Informs whether a bidirectional edge exists between two given vertices.
* ***gMixedGraphSearchUnidirectionalEdge*** : Informs whether a unidirectional edge exists from a source vertex to a destination vertex.
* ***gMixedGraphGetVertexDegree*** : Returns the degree (number of neighboring connections) of a given vertex.
* ***gMixedGraphSize*** : Enumerates and informs the total number of vertices present in the mixed graph.


## Usage Instructions
To include this repository locally in your project directory, follow these steps:
1. Open your project folder in the terminal.
2. Type the following command and press enter:
<ul>
    <li><code>git clone https://github.com/JamesStewart314/C-Language-Codes.git</code></li>
</ul>

Now, if everything went as expected, this repository should be present locally on your computer.

Finally, to include the mixed graph functionalities in your project, open your code in an IDE and add, at the top of the file — preferably adjacent to the already existing inclusion directives — the relative path to the header file that contains the prototypes of the mixed graph functions of this module. In the example given above, the specific path to include the header file in the "MainCode.c" code would be:

```c
#include "./Abstract Data Types for Generic Data/Graph/Mixed Graph/genMixedGraph.h"
```

Thus, after including the header file in your code with the #include preprocessor directive, the IDE will recognize the functions, which will be available for your respective use.

It is worth mentioning that your project's compilation process must include not only the codes already planned, but also the files containing the implementations of the functions declared in the header files. Since this module depends on the Linked List data structure, both implementation files must be attached to the compilation stage.

Here is an example, in the same context mentioned above, of how to compile the code "MainCode.c" using the GCC compiler, assuming that the Mixed Graph module was included and used in the code:

```c
gcc MainCode.c "./Abstract Data Types for Generic Data/Graph/Mixed Graph/genMixedGraph.c" "./Abstract Data Types for Generic Data/Linked List/genLinkedList.c" -o ExecutableProgram -I "./Abstract Data Types for Generic Data/Graph/Mixed Graph/" -I "./Abstract Data Types for Generic Data/Linked List/"
```

<div>
In the above command, we specified the following during the compilation process:

1. Main file: <code>MainCode.c</code> (there may be more than one C file in addition to this, depending on the project context).

2. Relative path to the module: <code>"./Abstract Data Types for Generic Data/Graph/Mixed Graph/genMixedGraph.c"</code>, which implements the mixed graph functionalities, along with its dependency <code>genLinkedList.c</code>.

3. Flag for executable name: <code>-o ExecutableProgram</code>, which defines the name of the resulting file after compilation.

4. Flags for the header file directories: <code>-I</code> flags for the Mixed Graph and Linked List directories, which indicate the directories containing the header files used.

</div>

For demonstration and clarification purposes, there will be comments adjacent to each function signature, briefly describing its behavior and purpose, contained in the header file (*genMixedGraph.h*). Furthermore, there is also a **commented program** that uses the data structure created in this module, in order to resolve any remaining doubts regarding its use, showing it in practice.
<br></br>

<div align="center">

## Algorithmic Complexity in Big O Notation for the Mixed Graph Operations:

| Operation                      | Time Complexity | Space Complexity |
|:------------------------------:|:---------------:|:----------------:|
| Clear                          | O(V + E)        | O(1)             |
| Copy                           | O(V + E)        | O(V + E)         |
| Create Edge                    | O(V)            | O(1)             |
| Create Unidirectional Edge     | O(V)            | O(1)             |
| Destroy                        | O(V + E)        | O(1)             |
| Equals                         | O(V² + E)       | O(1)             |
| Get Vertex Degree              | O(V)            | O(1)             |
| Impress                        | O(V + E)        | O(1)             |
| Insert Vertex                  | O(V)            | O(1)             |
| Is Empty                       | O(1)            | O(1)             |
| Remove Edge                    | O(V + E)        | O(1)             |
| Remove Unidirectional Edge     | O(V + E)        | O(1)             |
| Remove Vertex                  | O(V + E)        | O(1)             |
| Search Edge                    | O(V + E)        | O(1)             |
| Search Unidirectional Edge     | O(V + E)        | O(1)             |
| Search Vertex                  | O(V)            | O(1)             |
| Size                           | O(1)            | O(1)             |

*Where **V** = number of vertices and **E** = number of edges.*

</div>
