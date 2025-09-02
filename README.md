# CMPS 2200  Recitation 01

**Name (Team Member 1):** Hrishi Kabra  
**Name (Team Member 2):**_________________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`. All tests are in `test_main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest test_main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

**Linear Search** - worst case is when the key is not in the list as this forces you to check all n elements. If the key is present, then worst case is when it is at the last index as you still have to check all elements. 

**Binary Search** - worst case is also when the key is not in the list as this would also force you to check all n elements. It could also be when the key is at the two extreme ends - the first element or the last element.

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**Linear Search** - Best case is when the key is the first element in the list - index 0 - only one comparison is needed to find the target

**Binary Search** - Best case is when the key is at the middle index - also only one comparison needed to find the target

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest test_main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**Timing Results in Table**

|            n |   linear |   binary |
|--------------|----------|----------|
|       10.000 |    0.002 |    0.002 |
|      100.000 |    0.002 |    0.001 |
|     1000.000 |    0.014 |    0.002 |
|    10000.000 |    0.144 |    0.001 |
|   100000.000 |    1.436 |    0.004 |
|  1000000.000 |   14.564 |    0.007 |
| 10000000.000 |  161.555 |    0.010 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

Yes, the theoretical running times match the results - Linear search shows $O(n)$ behaviour - as the input size increases by 10x the running time increases by approx. 10x - linear growth. For binary search - running time remains low and grows slowly as the input size increases - logarithmic growth. This confirms that it matches the results.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **Each search would take $O(n)$ time - if you need to search $k$ times, that gives $O(kn)$**
  + For binary search? **The list needs to be sorted first - this has a time complexity of $O(n^2)$ - then you need to perform binary search $k$ times and each one takes $O(log_2(n))$ - totalling to $O(klog_2(n))$ - hence, in the end this gives a time complexity of $O(n^2 + klog_2(n))$**
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **Need to find when $n^2 + klog_2(n) \leq kn \rightarrow n^2 \leq kn - klog_2(n) \rightarrow n^2 \leq k(n - log_2(n))$ $\rightarrow$ $log_2(n)$ becomes much smaller than $n$ as $n$ increases - hence you can approximate $n^2 \leq kn$ $\rightarrow$ this is only true when $k \geq n$ $\rightarrow$ Hence, when $k \geq n$, it becomes more efficient to sort first and use binary search compared to using linear search. If $k < n$ then using linear search is more efficient.**
