---
description: >-
  Originally posted on Medium here -
  https://medium.com/@anandgaur2207/android-dsa-questions-for-interviews-with-answers-09bff9a1e4a2
---

# Android DSA Questions for Interviews with Answers

<figure><img src="https://miro.medium.com/v2/resize:fit:4800/format:webp/0*VM3wRtgPEuyXCYFi.png" alt=""><figcaption></figcaption></figure>

When preparing for Android developer interviews, you’re likely to encounter questions that test not only your Android development skills but also your problem-solving abilities in data structures and algorithms (DSA). These “puzzle-type” questions challenge your analytical thinking and programming knowledge, crucial for senior roles.

In this blog, we’ll explore some common DSA questions tailored to Android scenarios, along with their answers.

## 1. Optimize App Startup Using Data Structures <a href="#id-7e21" id="id-7e21"></a>

**Problem:**\
You are tasked with optimizing an app’s startup time. The app fetches a configuration file containing key-value pairs, which is frequently accessed during runtime. Write an algorithm to load the configuration quickly and retrieve any value in _O(1)_ time.

**Solution:** This is a classic use case for a **HashMap**, which provides _O(1)_ time complexity for lookups. Here’s how you can solve it:

**Code:**

```
fun loadConfigurations(configurations: List<Pair<String, String>>): Map<String, String> {
    val configMap = mutableMapOf<String, String>()
    for (config in configurations) {
        configMap[config.first] = config.second
    }
    return configMap
}

fun main() {
    val configurations = listOf("theme" to "dark", "fontSize" to "medium", "language" to "English")
    val configMap = loadConfigurations(configurations)
    println(configMap["theme"]) // Output: dark
}
```

## 2. Efficient Caching in Android <a href="#id-50cf" id="id-50cf"></a>

**Problem:**\
You need to design a caching mechanism for a news app to store articles and retrieve the most recently accessed article quickly. How would you implement this?

**Solution:**\
Use an **LRU Cache (Least Recently Used)**, which can be implemented using `LinkedHashMap` in Kotlin.

**Code:**

```
class LRUCache<K, V>(private val capacity: Int) : LinkedHashMap<K, V>(capacity, 0.75f, true) {
    override fun removeEldestEntry(eldest: MutableMap.MutableEntry<K, V>?): Boolean {
        return size > capacity
    }
}

fun main() {
    val cache = LRUCache<String, String>(3)
    cache["1"] = "Article 1"
    cache["2"] = "Article 2"
    cache["3"] = "Article 3"
    println(cache) // Output: {1=Article 1, 2=Article 2, 3=Article 3}
    cache["4"] = "Article 4" // This will remove the least recently used item
    println(cache) // Output: {2=Article 2, 3=Article 3, 4=Article 4}
}
```

## 3. Find Duplicate Images in a Gallery App <a href="#id-1f77" id="id-1f77"></a>

**Problem:**\
You are building a gallery app that identifies duplicate images. Each image has a unique hash (String). Write an algorithm to find duplicates.

**Solution:**\
Use a **Set** to track hashes as you iterate through the list of image hashes.

**Code:**

```
fun findDuplicates(hashes: List<String>): List<String> {
    val seen = mutableSetOf<String>()
    val duplicates = mutableListOf<String>()
    for (hash in hashes) {
        if (!seen.add(hash)) {
            duplicates.add(hash)
        }
    }
    return duplicates
}

fun main() {
    val imageHashes = listOf("hash1", "hash2", "hash3", "hash1", "hash4", "hash3")
    println(findDuplicates(imageHashes)) // Output: [hash1, hash3]
}
```

## 4. Schedule Notifications Using Algorithms <a href="#id-6677" id="id-6677"></a>

**Problem:**\
You need to schedule notifications for a user’s reminders in a way that notifications don’t overlap. Given a list of reminder times, write an algorithm to determine if they can be scheduled without conflict.

**Solution:**\
Sort the reminders by start time and check for overlaps using intervals.

**Code:**

```
data class Reminder(val start: Int, val end: Int)

fun canSchedule(reminders: List<Reminder>): Boolean {
    val sortedReminders = reminders.sortedBy { it.start }
    for (i in 1 until sortedReminders.size) {
        if (sortedReminders[i].start < sortedReminders[i - 1].end) {
            return false // Overlap detected
        }
    }
    return true
}

fun main() {
    val reminders = listOf(Reminder(1, 3), Reminder(2, 5), Reminder(6, 8))
    println(canSchedule(reminders)) // Output: false (due to overlap between 1-3 and 2-5)
}
```

## 5. Optimize RecyclerView Data Loading <a href="#id-914b" id="id-914b"></a>

**Problem:**\
You have a large dataset to display in a RecyclerView. How would you use an algorithm to fetch only the required data for display efficiently?

**Solution:**\
Implement **pagination** to load data in chunks using Android’s `PagedListAdapter`.

**Code:**\
This is implemented using a library such as Paging 3 in Android. Below is a pseudo-code outline:

```
// Repository
fun getPagedData(): Flow<PagingData<Item>> {
    return Pager(PagingConfig(pageSize = 20)) {
        MyPagingSource()
    }.flow
}

// PagingSource
class MyPagingSource : PagingSource<Int, Item>() {
    override suspend fun load(params: LoadParams<Int>): LoadResult<Int, Item> {
        val position = params.key ?: 0
        val data = fetchDataFromApi(position, params.loadSize)
        return LoadResult.Page(
            data = data,
            prevKey = if (position == 0) null else position - 1,
            nextKey = if (data.isEmpty()) null else position + 1
        )
    }
}
```

## 6. Merge Two Sorted Lists of App Data <a href="#id-2d9a" id="id-2d9a"></a>

**Problem:**\
You have two sorted lists of user data from two servers. Write an algorithm to merge them into one sorted list.

**Solution:**\
This is a classic **merge** problem, solvable using a two-pointer technique.

**Code:**

```
fun mergeSortedLists(list1: List<Int>, list2: List<Int>): List<Int> {
    val result = mutableListOf<Int>()
    var i = 0
    var j = 0

    while (i < list1.size && j < list2.size) {
        if (list1[i] <= list2[j]) {
            result.add(list1[i])
            i++
        } else {
            result.add(list2[j])
            j++
        }
    }

    while (i < list1.size) {
        result.add(list1[i])
        i++
    }

    while (j < list2.size) {
        result.add(list2[j])
        j++
    }

    return result
}

fun main() {
    val list1 = listOf(1, 3, 5)
    val list2 = listOf(2, 4, 6)
    println(mergeSortedLists(list1, list2)) // Output: [1, 2, 3, 4, 5, 6]
}
```

## 7. Find Missing App Data <a href="#id-0b2a" id="id-0b2a"></a>

**Problem:**\
In a list of sequential user IDs, one ID is missing. Write an algorithm to find the missing ID.

**Solution:**\
Use the sum formula for the first _n_ natural numbers: _**Sum=n×(n+1)/2**_

**Code:**

```
fun findMissingId(ids: List<Int>): Int {
    val n = ids.size + 1
    val expectedSum = n * (n + 1) / 2
    val actualSum = ids.sum()
    return expectedSum - actualSum
}

fun main() {
    val ids = listOf(1, 2, 3, 5)
    println(findMissingId(ids)) // Output: 4
}
```

## 8. Detect a Cycle in User Session Data <a href="#f587" id="f587"></a>

**Problem:**\
Given a linked list of user session data, detect if there’s a cycle in the list.

**Solution:**\
Use Floyd’s Cycle Detection Algorithm (**fast and slow pointer**).

**Code:**

```
class Node(var value: Int) {
    var next: Node? = null
}

fun hasCycle(head: Node?): Boolean {
    var slow = head
    var fast = head

    while (fast?.next != null) {
        slow = slow?.next
        fast = fast.next?.next

        if (slow == fast) return true
    }
    return false
}

fun main() {
    val head = Node(1)
    val second = Node(2)
    val third = Node(3)
    head.next = second
    second.next = third
    third.next = second // Creates a cycle
    println(hasCycle(head)) // Output: true
}
```

## 9. Optimize Network Requests <a href="#c92b" id="c92b"></a>

**Problem:**\
You need to debounce network requests in an app (e.g., a search bar). Write an algorithm to ignore multiple rapid inputs and only process the final one after a delay.

**Solution:**\
Implement **Debouncing** using `Handler` or `Coroutines`.

**Code Using Kotlin Coroutines:**

```
import kotlinx.coroutines.*

var searchJob: Job? = null

fun performDebouncedSearch(query: String, delayMs: Long = 300L) {
    searchJob?.cancel() // Cancel previous job if running
    searchJob = CoroutineScope(Dispatchers.Main).launch {
        delay(delayMs)
        performSearch(query) // Call actual search function here
    }
}

fun performSearch(query: String) {
    println("Searching for: $query")
}

fun main() {
    performDebouncedSearch("android")
    performDebouncedSearch("android dev")
    performDebouncedSearch("android developer") // Only this will execute after delay
}
```

## 10. Find the Kth Largest Element in App Metrics <a href="#de51" id="de51"></a>

**Problem:**\
Given a list of app performance metrics, find the _kth_ largest metric.

**Solution:**\
Use a **Min-Heap** for efficient retrieval of the _kth_ largest element.

**Code:**

```
import java.util.PriorityQueue

fun findKthLargest(nums: IntArray, k: Int): Int {
    val minHeap = PriorityQueue<Int>()
    for (num in nums) {
        minHeap.add(num)
        if (minHeap.size > k) {
            minHeap.poll()
        }
    }
    return minHeap.peek()
}

fun main() {
    val metrics = intArrayOf(3, 2, 1, 5, 6, 4)
    println(findKthLargest(metrics, 2)) // Output: 5
}
```

## 11. Check Palindrome in User Input <a href="#f209" id="f209"></a>

**Problem:**\
Write an algorithm to check if a user-input string is a palindrome.

**Solution:**\
Reverse the string and compare it to the original.

**Code:**

```
fun isPalindrome(input: String): Boolean {
    val sanitized = input.filter { it.isLetterOrDigit() }.lowercase()
    return sanitized == sanitized.reversed()
}

fun main() {
    println(isPalindrome("A man, a plan, a canal, Panama")) // Output: true
    println(isPalindrome("Hello")) // Output: false
}
```

## 12. Top K Frequent App Features Used <a href="#b680" id="b680"></a>

**Problem:**\
Given a list of features used by app users, return the top _K_ most frequently used features.

**Solution:**\
Use a **HashMap** for counting and a **PriorityQueue** for sorting.

**Code:**

```
fun topKFrequentFeatures(features: List<String>, k: Int): List<String> {
    val frequencyMap = features.groupingBy { it }.eachCount()
    val pq = PriorityQueue<Map.Entry<String, Int>>(compareBy { it.value })

    for (entry in frequencyMap.entries) {
        pq.add(entry)
        if (pq.size > k) {
            pq.poll()
        }
    }

    return pq.map { it.key }
}

fun main() {
    val features = listOf("login", "signup", "login", "profile", "login", "signup")
    println(topKFrequentFeatures(features, 2)) // Output: ["signup", "login"]
}
```

## 13. Longest Consecutive Sequence of User Activity <a href="#id-8cff" id="id-8cff"></a>

**Problem:**\
Given a list of integers representing user activity timestamps, find the length of the longest consecutive sequence.

**Solution:**\
Use a **HashSet** for quick lookups.

**Code:**

```
fun longestConsecutive(nums: IntArray): Int {
    val numSet = nums.toSet()
    var longest = 0

    for (num in numSet) {
        if (num - 1 !in numSet) { // Start of a sequence
            var currentNum = num
            var currentStreak = 1

            while (currentNum + 1 in numSet) {
                currentNum++
                currentStreak++
            }

            longest = maxOf(longest, currentStreak)
        }
    }
    return longest
}

fun main() {
    val timestamps = intArrayOf(100, 4, 200, 1, 3, 2)
    println(longestConsecutive(timestamps)) // Output: 4 (Sequence: 1, 2, 3, 4)
}
```

## 14. Calculate Maximum Concurrent Users <a href="#id-7f70" id="id-7f70"></a>

**Problem:**\
You are given a list of login and logout times for users. Write an algorithm to calculate the maximum number of users active at the same time.

**Solution:**\
This is a classic interval problem that can be solved using **sorting** and a **sweep-line technique**.

**Code:**

```
fun maxConcurrentUsers(times: List<Pair<Int, Int>>): Int {
    val events = mutableListOf<Pair<Int, Boolean>>()

    for (time in times) {
        events.add(time.first to true)  // Login event
        events.add(time.second to false) // Logout event
    }

    events.sortWith(compareBy({ it.first }, { !it.second })) // Sort by time, logouts before logins if same time

    var maxUsers = 0
    var currentUsers = 0

    for (event in events) {
        if (event.second) currentUsers++ else currentUsers--
        maxUsers = maxOf(maxUsers, currentUsers)
    }

    return maxUsers
}

fun main() {
    val times = listOf(1 to 5, 2 to 6, 4 to 8)
    println(maxConcurrentUsers(times)) // Output: 3
}
```

## 15. Rearrange App Screens to Avoid Repetition <a href="#id-592d" id="id-592d"></a>

**Problem:**\
Given a list of screen IDs, rearrange them so that no two adjacent screens are the same. If not possible, return an empty list.

**Solution:**\
Use a **max-heap** (priority queue) to organize screens by their frequency.

**Code:**

```
import java.util.PriorityQueue

fun rearrangeScreens(screens: List<String>): List<String> {
    val freqMap = screens.groupingBy { it }.eachCount()
    val pq = PriorityQueue<Map.Entry<String, Int>>(compareByDescending { it.value })
    pq.addAll(freqMap.entries)

    val result = mutableListOf<String>()
    var prev: Map.Entry<String, Int>? = null

    while (pq.isNotEmpty()) {
        val current = pq.poll()
        result.add(current.key)

        if (prev != null && prev.value > 0) {
            pq.offer(prev)
        }

        prev = current.copy(value = current.value - 1)
    }

    return if (result.size == screens.size) result else emptyList()
}

fun main() {
    val screens = listOf("A", "A", "B", "B", "C")
    println(rearrangeScreens(screens)) // Output: [A, B, A, C, B] or similar valid result
}
```

## 16. Count Unique App Users <a href="#id-796e" id="id-796e"></a>

**Problem:**\
You are given a list of user IDs, where each ID may appear multiple times. Write an algorithm to count the number of unique users.

**Solution:**\
Use a **HashSet** to store unique IDs.

**Code:**

```
fun countUniqueUsers(userIds: List<String>): Int {
    return userIds.toSet().size
}

fun main() {
    val userIds = listOf("user1", "user2", "user1", "user3", "user2")
    println(countUniqueUsers(userIds)) // Output: 3
}
```

## 17. Shortest Path Between App Features <a href="#id-6663" id="id-6663"></a>

**Problem:**\
Your app has a feature navigation graph represented as an adjacency list. Write an algorithm to find the shortest path between two features.

**Solution:**\
Use **Breadth-First Search (BFS)**.

**Code:**

```
fun shortestPath(graph: Map<String, List<String>>, start: String, end: String): Int {
    val queue = ArrayDeque<Pair<String, Int>>() // Pair of node and distance
    val visited = mutableSetOf<String>()

    queue.add(start to 0)

    while (queue.isNotEmpty()) {
        val (node, distance) = queue.removeFirst()
        if (node == end) return distance

        if (node !in visited) {
            visited.add(node)
            graph[node]?.forEach { neighbor ->
                queue.add(neighbor to distance + 1)
            }
        }
    }

    return -1 // No path found
}

fun main() {
    val graph = mapOf(
        "Home" to listOf("Profile", "Settings"),
        "Profile" to listOf("Home", "Gallery"),
        "Settings" to listOf("Home"),
        "Gallery" to listOf("Profile")
    )
    println(shortestPath(graph, "Home", "Gallery")) // Output: 2
}
```

## 18. Rotate App Content by K Positions <a href="#id-9230" id="id-9230"></a>

**Problem:**\
Rotate a list of app content (e.g., carousel items) to the right by _K_ positions.

**Solution:**\
Use modular arithmetic and slicing.

**Code:**

```
fun rotateContent(content: List<Int>, k: Int): List<Int> {
    val n = content.size
    val rotations = k % n
    return content.takeLast(rotations) + content.dropLast(rotations)
}

fun main() {
    val content = listOf(1, 2, 3, 4, 5)
    println(rotateContent(content, 2)) // Output: [4, 5, 1, 2, 3]
}
```

## 19. Generate All App Menu Combinations <a href="#id-457b" id="id-457b"></a>

**Problem:**\
You need to generate all possible combinations of app menu items for testing purposes.

**Solution:**\
Use **backtracking**.

**Code:**

```
fun generateCombinations(menuItems: List<String>): List<List<String>> {
    val result = mutableListOf<List<String>>()
    fun backtrack(start: Int, combination: MutableList<String>) {
        result.add(ArrayList(combination))
        for (i in start until menuItems.size) {
            combination.add(menuItems[i])
            backtrack(i + 1, combination)
            combination.removeAt(combination.size - 1)
        }
    }
    backtrack(0, mutableListOf())
    return result
}

fun main() {
    val menu = listOf("Home", "Profile", "Settings")
    println(generateCombinations(menu))
    // Output: [[], [Home], [Home, Profile], [Home, Profile, Settings], [Home, Settings], [Profile], [Profile, Settings], [Settings]]
}
```

## 20. Detect Anomalous App Usage Patterns <a href="#d55a" id="d55a"></a>

**Problem:**\
Given a list of app usage durations, identify if any user exceeds a threshold in total usage for the day.

**Solution:**\
Use a **HashMap** to aggregate usage and compare against the threshold.

**Code:**

```
fun detectAnomalousUsage(usageData: List<Pair<String, Int>>, threshold: Int): List<String> {
    val userUsageMap = mutableMapOf<String, Int>()

    for ((user, duration) in usageData) {
        userUsageMap[user] = userUsageMap.getOrDefault(user, 0) + duration
    }

    return userUsageMap.filter { it.value > threshold }.keys.toList()
}

fun main() {
    val usageData = listOf("user1" to 120, "user2" to 300, "user1" to 100, "user3" to 50)
    println(detectAnomalousUsage(usageData, 200)) // Output: [user1, user2]
}
```

## 21. Identify Circular Dependencies in Features <a href="#f79d" id="f79d"></a>

**Problem:**\
Given a graph of feature dependencies, determine if there is a cycle.

**Solution:**\
Use **DFS with a visited set**.

**Code:**

```
fun hasCycle(graph: Map<String, List<String>>): Boolean {
    val visited = mutableSetOf<String>()
    val stack = mutableSetOf<String>()

    fun dfs(node: String): Boolean {
        if (node in stack) return true
        if (node in visited) return false

        visited.add(node)
        stack.add(node)
        for (neighbor in graph[node] ?: emptyList()) {
            if (dfs(neighbor)) return true
        }
        stack.remove(node)
        return false
    }

    return graph.keys.any { dfs(it) }
}

fun main() {
    val featureGraph = mapOf(
        "Login" to listOf("Home"),
        "Home" to listOf("Profile"),
        "Profile" to listOf("Settings"),
        "Settings" to listOf("Home") // Cycle exists
    )
    println(hasCycle(featureGraph)) // Output: true
}
```

## Summary <a href="#id-7fd0" id="id-7fd0"></a>

DSA questions in Android interviews often test your ability to solve real-world app development problems efficiently. By combining data structure knowledge with Android-specific scenarios, you can demonstrate your expertise effectively. Practice these types of questions to build confidence and readiness for your next Android developer interview!

Thank you for reading. 🙌🙏✌.
