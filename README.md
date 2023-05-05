Download Link: https://assignmentchef.com/product/solved-cse12-assignment-3-deques-stacks-queues-and-search
<br>
In this assignment you will implement data structures that provide an implementation for three abstract data types:  A double-ended queue using a circular array, a stack and a queue.  In addition,  these data structures will be used in a game of Minesweeper (provided for you).  Also, along the way you will get more experience with implementing Java interfaces, writing JUnit test cases, and using the Adapter design pattern.

Part 1: Deque12 and BoundedDequeTester

BoundedDequeTester.java

Read the documentation in the source code file for the BoundedDeque&lt;E&gt; interface, or view the javadoc page for BoundedDeque which is included in the PR3 resources. Understand the responsibilities of each method required by the interface. Sketch a test plan for a class that implements this interface. Define a class named BoundedDequeTester that extends junit.framework.TestCase and that implements your test plan, using an Deque12 object as a test fixture.

We will run your tester as shown in lecture notes:

The class you will be testing is Deque12. Deque12 implements the BoundedDeque interface.  There is NO starter code for this particular class so you must write it yourself. <u>You should have</u> <u>at least one test for every method,</u> but it is better form to create multiple tests for some methods depending on the condition you are testing.  For example, you’ll probably want a separate test for adding to a full Deque from the test for adding to a non-full Deque.

As a practical matter, you do not need to completely write your BoundedDequeTester program before starting to define Deque12. In fact, an iterative test-driven development process can work well: write some tests in BoundedDequeTester, and implement the functionality in Deque12 that will be tested by those tests, test that functionality with BoundedDequeTester, write more tests, etc. The end result will (hopefully!) be the same: A good tester, and a good implementation of the class being tested.

As for previous (and future) assignments, make sure that your BoundedDequeTester does not depend on anything <em>not</em> specified by the documentation of the BoundedDeque interface and the Deque12 class. For example, do not make use of any other constructors or instance or static methods or variables that the ones required in the documentation.

<h1>Deque12.java</h1>

Define a <strong>public generic class Deque12&lt;E&gt; that implements the BoundedDeque&lt;E&gt; interface</strong>. Besides the requirements for the methods and constructor documented in that interface, for this assignment there is the additional requirement that <strong><em>this implementation must use a circular array to hold its elements</em></strong><strong>.</strong> (Note also that, as for other assignments, your Deque12 should not define any public methods or constructors other than those in the interface specification.)




A circular array can be rather tricky to implement correctly! It will be worth your time to sketch it out on paper before you start writing code.




You will of course need to create an array with length equal to the capacity of the Deque12 object. <strong>Because raw arrays don’t play nicely with generics, you should use an ArrayList object for this purpose.   However, there are a couple of subtleties to look out for when using an ArrayList instead of an array:</strong>

<ul>

 <li>Be careful with the difference between the ArrayList’s add method and its set method. You’ll almost certainly want to use set, not add.  But this means that you must add capacity items to your ArrayList before you do anything else (i.e. in the constructor), or set will throw an IndexOutOfBounds error.</li>

 <li>Remember that no matter what size you initialize your ArrayList, it can always be increased, so be careful not to accidentally grow your ArrayList beyond your BoundedDeque’s capacity. Once your Deque12 instance has been properly constructed, If you only use set and not add, you should not run into this problem.</li>

</ul>




You will want to have instance variables for the size of the Deque12 (how many data elements it is currently holding), and to indicate which elements of the array are the current front and back elements. Think about what the values of these instance variables should be if the Deque12 is empty, or has one element, or is full (has size equal to its capacity). And in each case, think carefully about what needs to change for an element to be added or removed from the front or the back. Different solutions are possible, as long as all the design decisions you make are consistent with each other, and with the requirements of the interface you are implementing.

Part 2: Queue12

Now that you have your Deque built and fully tested, you will use it to implement a Stack and a Queue.

<h1>Stack12.java</h1>

We have provided a full implementation of Stack12.java that <em>adapts </em> Deque12 using the adapter design pattern. It is liberally documented so that you can see what a fully-documented code really looks like. Read and understand the interface specification in BoundedStack.java (or view the javadoc page for BoundedStack which is included in the PR3 resources).  We’ve provided you with some unit tests that you can use to test that Stack12 behaves properly with YOUR implementation of Deque12.  Note that the methods required by the BoundedStack interface are different from, though closely related to, the BoundedDeque interface methods.

<h1>Queue12.java</h1>

Read and understand the interface specification in BoundedQueue.java (or view the javadoc page for BoundedQueue which is included in the PR3 resources) and then define a generic class Queue12&lt;E&gt; that implements the BoundedQueue&lt;E&gt; interface. Use the existing Stack12 as a guide and adapt Deque12 to Implement Queue12. Again note that the methods required by the BoundedQueue interface are different from, though closely related to, the BoundedDeque interface methods, and so the Adapter pattern is applicable here as well.




As is often the case when the Adapter pattern is used, if the adapted class (Deque12 in this case) is tested and debugged, the adapting class shouldn’t need much testing, because almost all of the work is being handled by delegation to the adapted class’s methods. We provide you with a few simple tests which should be sufficient.




You must properly document your Queue12.java using javadoc in a similar manner to the provided Stack12.  Including pre-conditions and the like is good practice in writing “real documentation”




Part 3: Minesweeper, Depth First Search and Breadth First

Search

The last part of this assignment is to make sure that YOUR implementation of Deque12 and the adapted classes Stack12 and Queue12 work properly from an application’s viewpoint.  Provided to you in the implementation of a program that implements the popular game of Minesweeper

<a href="http://minesweeperonline.com/">(</a><a href="http://minesweeperonline.com/">http://minesweeperonline.com/</a><a href="http://minesweeperonline.com/">)</a>.  If you’ve never played Minesweeper take a few minutes to familiarize yourself with the game by playing a little bit.  But just a little bit… try not to get too distracted!




We’ve provided to you a very basic implementation of Minesweeper that is reasonably complete.  When you click on a cell with 0 mined neighbors, the game is supposed to automatically expose all of the surrounding neighbors of that cell, and then if any of those have no neighbors, it auto-exposes all of its neighbors, etc, until all of the connected cells with no mined neighbors and all of their connected neighbors are exposed.




Implementing this functionality is done by searching outward from the first exposed cell, expanding the search until all connected neighbors that should be exposed have been explored.  As we saw/will see in class on Thursday/Friday, this can be done using depth first search or breadth first search, and the only difference between the two algorithms is whether you use a stack or a queue as your data store during the search.




We have provided an implementation of both DFS and BFS for you.  Once you have your Queue12 class working, you can run and play the game  STUDY the difference between the behavior of the two algorithms (DFS vs. BFS).




<h1>Part A</h1>

The first step is to understand the provided code.  In your PR3.pdf file, Answer the following questions:

<ol>

 <li>Which method is called when the user clicks on one of the cells in the grid?</li>

 <li>What are the two central classes used to implement Minesweeper? Roughly, what does each do?</li>

 <li>What class implements the necessary MouseListener methods that are attached to each of the cells in the board?</li>

 <li>What does the exposeSlowly method do? How do you control the animation speed?</li>

 <li>What is the purpose of the actionPerformed method implemented in the MineSweeperGUI class?</li>

</ol>




These questions are a minimum starting point.  If you don’t understand what’s happening in the code, talk about it with your classmates (this is allowed) or go see a tutor, TA or professor.

<h1>Part B</h1>

Finally, explore the difference between the two algorithms.  Play the game with each algorithm, and notice how the animation changes.  In your PR3.pdf file in a section labeled <strong>Part B</strong>  describe the difference you see between how the cells are exposed when you use depth first search vs. breadth first search.




Just for fun!

Our version of Minesweeper is very basic, lacking creativity and many of the bells and whistles of the original game or improvements that you could imagine.  If you’re interested, improve on the game.  This is a boundlessly open ended extension, so have fun!


