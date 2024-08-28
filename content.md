# Longest Consecutive Sequence 🍡

### [Here is a video for this lesson](https://www.youtube.com/watch?v=y6z69mNbW28)

## The Problem
Write a program that:
- takes an unsorted array of integers
- returns the length of the longest consecutive elements sequence regardless of order

Your algorithm must run in O(n) time, making efficient use of data structures to achieve this performance.

## Understand the Problem
Before diving into the main problem, let's explore a simpler scenario to get familiar with the concept of identifying consecutive sequences in an array.

- Consider the array `[1, 7, 9, 10, 11, 3, 2, 4, 5]`. What is the longest consecutive elements sequence you can find here?
- (1, 2, 3, 4, 5)
  - Correct! The sequence of `1, 2, 3, 4, 5` is consecutive and has a length of 5.
- (7, 9, 10, 11)
  - Incorrect. While `7, 9, 10, 11` are in close numerical order, they are not consecutive numbers. The sequence skips 8, breaking the consecutive streak.
- (9, 10, 11)
  - Incorrect. Although `9, 10, 11` are consecutive, there is a longer consecutive sequence in the array. Always look for the longest possible sequence.
- (1, 3, 5)
  - Incorrect. This sequence misses several numbers and does not represent the longest consecutive sequence. Remember, we are looking for the longest unbroken streak of increasing numbers.
{: .choose_best #longest_sequence title="Consider the array `[1, 7, 9, 10, 11, 3, 2, 4, 5]`. What is the longest consecutive elements sequence you can find here?" points="1" answer="1" }

Keep this exploration in mind as you approach the coding challenge. Ensure your solution can handle various arrays effectively and efficiently.

## Think Aloud
In coding interviews, demonstrating your problem-solving process is crucial. Discuss your approach, considering the efficiency and why you choose a particular data structure. Start with a simple, perhaps brute-force approach, and then refine it to meet the time complexity requirement.

## Test your code

```ruby
nums = [
  [100, 4, 200, 1, 3, 2],
  [0, 3, 7, 2, 5, 8, 4, 6, 0, 1],
  [10, 5, 12, 3]
]
array = nums.sample
# write your program using this method
def longest_consecutive(nums)

end

puts longest_consecutive(array)
```
{: .repl #longest_consecutive_sequence title="Longest Consecutive Sequence" readonly_lines="[1,2,3,4,5,6,8]"}

```ruby
describe "Longest Consecutive Sequence" do
  it "finds the longest consecutive sequence in the array [100, 4, 200, 1, 3, 2]" do
    result = longest_consecutive([100, 4, 200, 1, 3, 2])
    expect(result).to eq(4) # The sequence is 1, 2, 3, 4
  end
end
```
{: .repl-test #longest_consecutive_sequence_test_1 for="longest_consecutive_sequence" title="Longest Consecutive Sequence finds the sequence in array [100, 4, 200, 1, 3, 2]" points="1"}

```ruby
describe "Longest Consecutive Sequence" do
  it "finds the longest consecutive sequence in the array [0, 3, 7, 2, 5, 8, 4, 6, 0, 1]" do
    result = longest_consecutive([0, 3, 7, 2, 5, 8, 4, 6, 0, 1])
    expect(result).to eq(9) # The sequence is 0, 1, 2, 3, 4, 5, 6, 7, 8
  end
end
```
{: .repl-test #longest_consecutive_sequence_test_2 for="longest_consecutive_sequence" title="Longest Consecutive Sequence finds the sequence in array [0, 3, 7, 2, 5, 8, 4, 6, 0, 1]" points="1"}

```ruby
describe "Longest Consecutive Sequence" do
  it "finds the longest consecutive sequence in the array [10, 5, 12, 3]" do
    result = longest_consecutive([10, 5, 12, 3])
    expect(result).to eq(1) # No sequentials
  end
end
```
{: .repl-test #longest_consecutive_sequence_test_3 for="longest_consecutive_sequence" title="Longest Consecutive Sequence finds the sequence in array [10, 5, 12, 3]" points="1"}

```ruby
describe "Longest Consecutive Sequence" do
  it "handles a large array efficiently, suggesting O(n) time complexity" do
    large_array = (1..100000).to_a.shuffle
    start_time = Time.now
    result = longest_consecutive(large_array)
    end_time = Time.now
    expect(result).to eq(100000) # The sequence is the entire array
    expect(end_time - start_time).to be < 1 # Expect the test to run in under 1 second as an indication of O(n) complexity
  end
end
```
{: .repl-test #longest_consecutive_sequence_test_4 for="longest_consecutive_sequence" title="Longest Consecutive Sequence handles a large array efficiently, suggesting O(n) time complexity" points="1"}

## Tips and Clues for Solving the Problem
- **Set**: Using a [Set](https://ruby-doc.org/stdlib-2.5.3/libdoc/set/rdoc/Set.html) is key to achieving the O(n) time complexity. Start by converting the array to a Set for quick access.
- **Finding Sequences**: Iterate through the array, and for each element, check if it is the start of a sequence (i.e., there is no element in the set that is one less than the current element). If it is, then count how many consecutive numbers can be found starting with this number, updating the longest sequence length as necessary.
- **Edge Cases**: Consider what happens with duplicate numbers, very large or very small arrays, or arrays with widely varying numbers.
- **Efficiency**: Remember, the goal is to keep your solution within O(n) time complexity. This means efficiently using the set to avoid unnecessary iterations.

## Quiz
- What advantage does using a Set provide in solving this problem?
- It allows for quick determination of whether a specific element exists
  - Correct! Sets provide constant time complexity (O(1)) for lookups, which is crucial for maintaining overall O(n) time complexity.
- It helps in sorting the array
  - Incorrect. While sets are useful for many purposes, they do not help in sorting an array.
- It offers a way to easily encrypt the array data
  - Incorrect. sets are used for storing unique elements for quick access, not for encrypting data.
- It ensures that duplicate elements are automatically removed
  - Partially correct. While a set does remove duplicates, the key benefit in this context is the efficient access and check for consecutive sequences.
{: .choose_best #hash_set_advantage title="What advantage does using a set provide in solving this problem?" points="1" answer="1" }

- In the context of this problem, what is the significance of checking if an element is the start of a sequence?
- It prevents counting sequences more than once
  - Correct! This ensures each sequence is only counted from its beginning, avoiding overcounting and inefficiencies.
- It allows for elements to be sorted more quickly
  - Incorrect. While important for the algorithm's logic, this check does not directly relate to sorting the array.
- It is necessary for adding elements to the set
  - Incorrect. Elements are typically added to the set before this check, which is focused on identifying the start of sequences.
- It ensures that all elements are unique
  - Incorrect. Uniqueness is guaranteed by the nature of the set itself; this check is about identifying sequence starts.
{: .choose_best #sequence_start_significance title="In the context of this problem, what is the significance of checking if an element is the start of a sequence?" points="1" answer="1" }

## Conclusion
In this module, we've tackled the challenge of finding the longest consecutive sequence in an unsorted array of integers. By leveraging the power of sets, we explored how to access and manipulate data efficiently, enabling us to solve the problem within the desired O(n) time complexity.

Understanding and applying these concepts not only aids in solving similar problems but also enhances our ability to think about algorithms in terms of time and space efficiency. As you continue to practice with different data structures and algorithms, keep in mind the importance of selecting the right tool for the task and optimizing your approach for efficiency.

Remember, mastering these skills takes time and practice. Continue to experiment with different problems, always looking for ways to improve both your understanding and your code's performance.

## Resources
- [Set](https://ruby-doc.org/stdlib-2.5.3/libdoc/set/rdoc/Set.html)
