---
description: >-
  Originally posted in Medium here -
  https://medium.com/@anandgaur2207/top-most-asked-coding-questions-in-android-interviews-289ccb9c58d2
---

# Top Most Asked Coding Questions in Android Interviews

<figure><img src="../.gitbook/assets/0_NVegbq2M4Dm0JPmP.webp" alt=""><figcaption></figcaption></figure>

Preparing for an Android interview can be daunting, especially with the technical coding questions that test your Android fundamentals and Kotlin skills. Here are some of the most frequently asked coding questions in Android interviews, along with Kotlin code examples.

## 1. Reverse a String <a href="#id-83d0" id="id-83d0"></a>

```
fun reverseString(input: String): String {
    return input.reversed()
}

val result = reverseString("Android")
println(result)  // Output: diordnA
```

## 2. Check for Palindrome String <a href="#id-68a0" id="id-68a0"></a>

```
fun isPalindrome(input: String): Boolean {
    val reversed = input.reversed()
    return input == reversed
}

val result = isPalindrome("madam")
println(result)  // Output: true
```

## 3. Find the Maximum Element in an Array <a href="#c059" id="c059"></a>

```
fun findMax(arr: Array<Int>): Int? {
    return arr.maxOrNull()
}

val result = findMax(arrayOf(1, 3, 5, 7, 2))
println(result)  // Output: 7
```

## 4. FizzBuzz Problem <a href="#bda2" id="bda2"></a>

```
fun fizzBuzz(n: Int) {
    for (i in 1..n) {
        when {
            i % 15 == 0 -> println("FizzBuzz")
            i % 3 == 0 -> println("Fizz")
            i % 5 == 0 -> println("Buzz")
            else -> println(i)
        }
    }
}

fizzBuzz(15)
```

## 5. Count Vowels in a String <a href="#d5a4" id="d5a4"></a>

```
fun countVowels(input: String): Int {
    return input.count { it in "aeiouAEIOU" }
}

val result = countVowels("Hello World")
println(result)  // Output: 3
```

## 6. Remove Duplicates from a List <a href="#d1da" id="d1da"></a>

```
fun removeDuplicates(numbers: List<Int>): List<Int> {
    return numbers.distinct()
}

val result = removeDuplicates(listOf(1, 2, 2, 3, 4, 4, 5))
println(result)  // Output: [1, 2, 3, 4, 5]
```

## 7. Find the First Non-Repeated Character in a String <a href="#id-9142" id="id-9142"></a>

```
fun firstNonRepeatedCharacter(input: String): Char? {
    val charCount = mutableMapOf<Char, Int>()
    input.forEach { char -> charCount[char] = charCount.getOrDefault(char, 0) + 1 }
    return input.find { char -> charCount[char] == 1 }
}

val result = firstNonRepeatedCharacter("swiss")
println(result)  // Output: w
```

## 8. Implement a Basic Singleton in Kotlin <a href="#id-102d" id="id-102d"></a>

```
object AppConfig {
    var theme: String = "Light"
    var language: String = "English"

    fun showConfig() {
        println("Theme: $theme, Language: $language")
    }
}

AppConfig.theme = "Dark"
AppConfig.showConfig()  // Output: Theme: Dark, Language: English
```

## 9. Detect a Loop in a Linked List <a href="#ad2b" id="ad2b"></a>

```
class ListNode(val value: Int) {
    var next: ListNode? = null
}

fun hasCycle(head: ListNode?): Boolean {
    var slow = head
    var fast = head
    while (fast?.next != null) {
        slow = slow?.next
        fast = fast.next?.next
        if (slow == fast) return true
    }
    return false
}

// Example usage:
val node1 = ListNode(1)
val node2 = ListNode(2)
val node3 = ListNode(3)
node1.next = node2
node2.next = node3
node3.next = node1  // Creates a cycle

println(hasCycle(node1))  // Output: true
```

## 10. Factorial Using Recursion <a href="#eec2" id="eec2"></a>

```
fun factorial(n: Int): Int {
    return if (n <= 1) 1 else n * factorial(n - 1)
}

val result = factorial(5)
println(result)  // Output: 120
```

## 11. Find the Second Largest Element in an Array <a href="#id-5339" id="id-5339"></a>

```
fun secondLargest(arr: Array<Int>): Int? {
    val sortedArr = arr.distinct().sorted()
    return if (sortedArr.size > 1) sortedArr[sortedArr.size - 2] else null
}

val result = secondLargest(arrayOf(1, 3, 4, 2, 5))
println(result)  // Output: 4
```

## 12. Sum of Digits in a Number <a href="#f92b" id="f92b"></a>

```
fun sumOfDigits(n: Int): Int {
    return n.toString().map { it.toString().toInt() }.sum()
}

val result = sumOfDigits(12345)
println(result)  // Output: 15
```

## 13. Find the Missing Number in an Array <a href="#ae72" id="ae72"></a>

```
fun findMissingNumber(arr: Array<Int>, n: Int): Int {
    val totalSum = (n * (n + 1)) / 2
    val arrSum = arr.sum()
    return totalSum - arrSum
}

val result = findMissingNumber(arrayOf(1, 2, 4, 5), 5)
println(result)  // Output: 3
```

## 14. Check if Two Strings Are Anagrams <a href="#id-4090" id="id-4090"></a>

```
fun areAnagrams(str1: String, str2: String): Boolean {
    return str1.toCharArray().sorted() == str2.toCharArray().sorted()
}

val result = areAnagrams("listen", "silent")
println(result)  // Output: true
```

## 15. Flatten a Nested List of Integers <a href="#id-3566" id="id-3566"></a>

```
fun flatten(list: List<List<Int>>): List<Int> {
    return list.flatten()
}

val result = flatten(listOf(listOf(1, 2), listOf(3, 4), listOf(5, 6)))
println(result)  // Output: [1, 2, 3, 4, 5, 6]
```

## 16. Check if a Number is Prime <a href="#id-159a" id="id-159a"></a>

```
fun isPrime(n: Int): Boolean {
    if (n <= 1) return false
    for (i in 2..Math.sqrt(n.toDouble()).toInt()) {
        if (n % i == 0) return false
    }
    return true
}

val result = isPrime(7)
println(result)  // Output: true
```

## 17. Merge Two Sorted Arrays <a href="#c296" id="c296"></a>

```
fun mergeSortedArrays(arr1: Array<Int>, arr2: Array<Int>): Array<Int> {
    return (arr1 + arr2).sortedArray()
}

val result = mergeSortedArrays(arrayOf(1, 3, 5), arrayOf(2, 4, 6))
println(result.joinToString())  // Output: 1, 2, 3, 4, 5, 6
```

## 18. Find Common Elements in Two Arrays <a href="#fa39" id="fa39"></a>

```
fun findCommonElements(arr1: Array<Int>, arr2: Array<Int>): Array<Int> {
    return arr1.intersect(arr2.toSet()).toTypedArray()
}

val result = findCommonElements(arrayOf(1, 2, 3, 4), arrayOf(3, 4, 5, 6))
println(result.joinToString())  // Output: 3, 4
```

## 19. Sort a List of Strings by Length <a href="#c22a" id="c22a"></a>

```
fun sortByLength(strings: List<String>): List<String> {
    return strings.sortedBy { it.length }
}

val result = sortByLength(listOf("apple", "banana", "cherry", "kiwi"))
println(result.joinToString())  // Output: kiwi, apple, banana, cherry
```

## 20. Find the Intersection of Two Arrays <a href="#id-14e9" id="id-14e9"></a>

```
fun intersectArrays(arr1: Array<Int>, arr2: Array<Int>): Array<Int> {
    return arr1.filter { it in arr2 }.toTypedArray()
}

val result = intersectArrays(arrayOf(1, 2, 3, 4), arrayOf(3, 4, 5, 6))
println(result.joinToString())  // Output: 3, 4
```

## 21. Find the Largest Palindrome in a String <a href="#id-90ba" id="id-90ba"></a>

```
fun largestPalindrome(input: String): String {
    var largestPalindrome = ""
    
    for (i in input.indices) {
        for (j in i + 1..input.length) {
            val substring = input.substring(i, j)
            if (substring == substring.reversed() && substring.length > largestPalindrome.length) {
                largestPalindrome = substring
            }
        }
    }
    return largestPalindrome
}

val result = largestPalindrome("babad")
println(result)  // Output: bab (or aba)
```

## 22. Find the Missing Character in a String <a href="#d5ce" id="d5ce"></a>

```
fun findMissingCharacter(input: String): Char? {
    val fullAlphabet = "abcdefghijklmnopqrstuvwxyz"
    for (char in fullAlphabet) {
        if (char !in input) return char
    }
    return null
}

val result = findMissingCharacter("thequickbrownfoxjumpsoverlazydog")
println(result)  // Output: 's' (if 's' was missing)
```

## 23. Count Occurrences of Each Character in a String <a href="#id-8797" id="id-8797"></a>

```
fun countCharacterOccurrences(input: String): Map<Char, Int> {
    return input.groupingBy { it }.eachCount()
}

val result = countCharacterOccurrences("hello")
println(result)  // Output: {h=1, e=1, l=2, o=1}
```

## 24. Find the Longest Substring Without Repeating Characters <a href="#id-9164" id="id-9164"></a>

```
fun longestSubstringWithoutRepeating(input: String): String {
    var start = 0
    var maxLength = 0
    var maxSubstring = ""
    val charSet = mutableSetOf<Char>()
    
    for (end in input.indices) {
        while (input[end] in charSet) {
            charSet.remove(input[start])
            start++
        }
        charSet.add(input[end])
        if (end - start + 1 > maxLength) {
            maxLength = end - start + 1
            maxSubstring = input.substring(start, end + 1)
        }
    }
    return maxSubstring
}

val result = longestSubstringWithoutRepeating("abcabcbb")
println(result)  // Output: "abc"
```

## 25. Find the Element That Appears Once in an Array <a href="#id-6bc4" id="id-6bc4"></a>

```
fun findSingleElement(arr: Array<Int>): Int {
    return arr.reduce { acc, num -> acc xor num }
}

val result = findSingleElement(arrayOf(4, 1, 2, 1, 2))
println(result)  // Output: 4
```

## 26. Generate Fibonacci Sequence Up to n <a href="#c090" id="c090"></a>

```
fun generateFibonacci(n: Int): List<Int> {
    val fibonacci = mutableListOf(0, 1)
    for (i in 2 until n) {
        fibonacci.add(fibonacci[i - 1] + fibonacci[i - 2])
    }
    return fibonacci
}

val result = generateFibonacci(10)
println(result)  // Output: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

## 27. Find the Maximum Product of Two Integers in an Array <a href="#bc9a" id="bc9a"></a>

```
fun maxProduct(arr: Array<Int>): Int {
    val sortedArr = arr.sorted()
    return sortedArr[sortedArr.size - 1] * sortedArr[sortedArr.size - 2]
}

val result = maxProduct(arrayOf(1, 3, 5, 7, 9))
println(result)  // Output: 63
```

## 28. Check if a String is a Valid Number <a href="#id-8de4" id="id-8de4"></a>

```
fun isValidNumber(input: String): Boolean {
    return input.toDoubleOrNull() != null
}

val result = isValidNumber("123.45")
println(result)  // Output: true
```

## 29. Find the First Non-Repeated Character in a String <a href="#id-3eac" id="id-3eac"></a>

```
fun firstNonRepeatedChar(input: String): Char? {
    val charCount = input.groupingBy { it }.eachCount()
    return input.find { charCount[it] == 1 }
}

val result = firstNonRepeatedChar("swiss")
println(result)  // Output: w
```

## 30. Find the Duplicates in an Array <a href="#id-260f" id="id-260f"></a>

```
fun findDuplicates(arr: Array<Int>): List<Int> {
    val seen = mutableSetOf<Int>()
    val duplicates = mutableListOf<Int>()
    
    for (num in arr) {
        if (num in seen) {
            duplicates.add(num)
        } else {
            seen.add(num)
        }
    }
    
    return duplicates
}

val result = findDuplicates(arrayOf(1, 2, 3, 4, 2, 5, 3))
println(result.joinToString())  // Output: 2, 3
```

## 31. Find the Majority Element in an Array <a href="#id-87bf" id="id-87bf"></a>

```
fun majorityElement(nums: Array<Int>): Int {
    var count = 0
    var candidate = 0
    
    for (num in nums) {
        if (count == 0) candidate = num
        count += if (num == candidate) 1 else -1
    }
    
    return candidate
}

val result = majorityElement(arrayOf(3, 3, 4, 2, 4, 4, 2, 4, 4))
println(result)  // Output: 4
```

## 32. Find All Permutations of a String <a href="#ad9b" id="ad9b"></a>

```
fun permute(str: String): List<String> {
    if (str.length == 1) return listOf(str)
    
    val result = mutableListOf<String>()
    for (i in str.indices) {
        val char = str[i]
        val remaining = str.substring(0, i) + str.substring(i + 1)
        for (perm in permute(remaining)) {
            result.add(char + perm)
        }
    }
    return result
}

val result = permute("abc")
println(result.joinToString())  // Output: abc, acb, bac, bca, cab, cba
```

## 33. Find the Missing Number in an Array of Consecutive Numbers <a href="#id-5c38" id="id-5c38"></a>

```
fun findMissingNumber(arr: IntArray): Int {
    val n = arr.size + 1
    val totalSum = n * (n + 1) / 2
    val arrSum = arr.sum()
    return totalSum - arrSum
}

val result = findMissingNumber(intArrayOf(1, 2, 4, 5, 6))
println(result)  // Output: 3
```

## 34. Find the Longest Common Prefix of a List of Strings <a href="#id-34f9" id="id-34f9"></a>

```
fun longestCommonPrefix(strs: List<String>): String {
    if (strs.isEmpty()) return ""
    var prefix = strs[0]
    
    for (str in strs) {
        while (!str.startsWith(prefix)) {
            prefix = prefix.dropLast(1)
            if (prefix.isEmpty()) return ""
        }
    }
    return prefix
}

val result = longestCommonPrefix(listOf("flower", "flow", "flight"))
println(result)  // Output: "fl"
```

## 35. Merge Alternating Characters from Two Strings <a href="#id-163d" id="id-163d"></a>

```
fun mergeStrings(a: String, b: String): String {
    val result = StringBuilder()
    val length = minOf(a.length, b.length)

    // Iterate through both strings and add alternating characters to the result
    for (i in 0 until length) {
        result.append(a[i])
        result.append(b[i])
    }

    // If 'a' is longer, append the remaining characters
    if (a.length > b.length) {
        result.append(a.substring(length))
    }

    // If 'b' is longer, append the remaining characters
    if (b.length > a.length) {
        result.append(b.substring(length))
    }

    return result.toString()
}

fun main() {
    val a = "abcd"
    val b = "1234"
    val output = mergeStrings(a, b)
    println(output)  // Output: a1b2c3d4
}
```

## 36. Find the Third Largest Element in an Array <a href="#b91c" id="b91c"></a>

```
fun thirdLargestElement(arr: IntArray): Int? {
    if (arr.size < 3) return null  // Return null if there are fewer than 3 elements

    var first = Int.MIN_VALUE
    var second = Int.MIN_VALUE
    var third = Int.MIN_VALUE

    for (num in arr) {
        if (num > first) {
            third = second
            second = first
            first = num
        } else if (num > second && num != first) {
            third = second
            second = num
        } else if (num > third && num != second) {
            third = num
        }
    }

    return if (third != Int.MIN_VALUE) third else null
}

fun main() {
    val arr = intArrayOf(12, 35, 1, 10, 34, 1)
    val result = thirdLargestElement(arr)
    if (result != null) {
        println("The third largest element is: $result")
    } else {
        println("Array has fewer than 3 distinct elements.")
    }
}
```

## 37. Check if One Array is a Subset of Another <a href="#id-2430" id="id-2430"></a>

```
fun isSubset(arr1: IntArray, arr2: IntArray): Boolean {
    // Convert arr1 to a set for faster lookup
    val set1 = arr1.toHashSet()

    // Check if each element of arr2 is in arr1
    for (element in arr2) {
        if (!set1.contains(element)) {
            return false  // arr2 contains an element not in arr1
        }
    }
    return true  // All elements of arr2 are in arr1
}

fun main() {
    val arr1 = intArrayOf(1, 2, 3, 4, 5)
    val arr2 = intArrayOf(2, 4, 5)

    val result = isSubset(arr1, arr2)
    if (result) {
        println("arr2 is a subset of arr1.")
    } else {
        println("arr2 is NOT a subset of arr1.")
    }
}
```

Thank you for reading. 🙌🙏✌.
