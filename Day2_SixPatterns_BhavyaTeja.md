## Pattern 1 – Persona

### Prompt

You are a senior placement coach at Aditya University. You have prepared 200 B.Tech CSE students for TCS, Infosys, and Cognizant placement interviews. A 3rd-year CSE student with 7.5 CGPA asks you about Big-O notation. Explain it the way you would in a 1-on-1 prep session — concrete, conversational, exam-relevant.

### Output

Alright, great question — and honestly, this is one of the topics that separates students who just "know" DSA from students who _understand_ it. Interviewers at TCS and Infosys ask this not just as a theory question — they use it to check if you can reason about your own code.

Let me break it down the way I'd explain it to you one-on-one.

---

**Think of Big-O as the "worst-case speed rating" of your code.**

Imagine you have a list of 1,000 student names and you're searching for someone. How many steps does your code take? That's what Big-O measures — not in seconds (that depends on your laptop), but in _number of operations relative to input size_. We call that input size **n**.

Here's the key mental model: **Big-O asks "as n grows huge, how does my work grow?"**

We drop constants and small terms — because if n is a million, the difference between `2n` and `3n` is trivial. What matters is the _shape_ of the curve.Now let me walk you through each one with a **real code example** — the kind you'd actually write in an interview.

---

**O(1) — Constant time** _(the dream)_

```python
def get_first(arr):
    return arr[0]
```

Doesn't matter if the array has 10 or 10 million elements. One step. Always. Accessing a hashmap by key is also O(1) — this is why interviewers love "use a dictionary" solutions.

---

**O(log n) — Logarithmic** _(very fast, shows up in Binary Search)_

```python
def binary_search(arr, target):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target: return mid
        elif arr[mid] < target: low = mid + 1
        else: high = mid - 1
```

With 1,000 elements, you need at most ~10 steps. With 1,000,000 elements? Only ~20 steps. It _halves_ the problem each time. **Remember: log n always means "halving" — think Binary Search.**

---

**O(n) — Linear** _(acceptable — you touched everything once)_

```python
def find_max(arr):
    max_val = arr[0]
    for x in arr:
        if x > max_val:
            max_val = x
    return max_val
```

One loop. You go through the list once. 1,000 elements = 1,000 steps. Clean and honest.

---

**O(n log n) — "Good" sorting** _(Merge Sort, Quick Sort)_

This is what Python's `sorted()` uses internally. When an interviewer asks "what's the best time complexity for sorting?", this is your answer. You can't sort faster than O(n log n) with comparison-based algorithms — that's a proven mathematical fact, which impresses interviewers when you say it.

---

**O(n²) — Quadratic** _(the danger zone — spot and fix these)_

```python
def has_duplicate(arr):
    for i in range(len(arr)):
        for j in range(len(arr)):
            if i != j and arr[i] == arr[j]:
                return True
    return False
```

Nested loops = almost always O(n²). With 1,000 elements: one million steps. With 10,000: a hundred million. **This is what Infosys and TCS will ask you to optimize.** The better solution? Use a `set` — O(n).

---

**The one question that always comes up in interviews:**

_"What is the time complexity of your solution?"_

Here's how to answer confidently — look for these patterns in your code:

| What you see in code        | Complexity |
| --------------------------- | ---------- |
| Single loop                 | O(n)       |
| Loop inside a loop          | O(n²)      |
| Halving the input each step | O(log n)   |
| Loop + Binary Search inside | O(n log n) |
| No loop, just indexing/math | O(1)       |

---

**One more thing that catches students off guard** — Space complexity. Big-O also applies to _memory_, not just time. If you create a new array of size n inside your function, that's O(n) space. Interviewers at Cognizant especially ask: _"Can you solve this in O(1) space?"_ — meaning, without creating extra data structures.

---

Self Score: 5/5

---

## Pattern 2 – Few-Shot

### Prompt

> "Here are example explanations from a placement coach:
>
> Q: What is recursion?
> A: A function calling itself with a smaller problem. Like Russian dolls — open one, find a smaller one inside. Stops at base case. Example: factorial.
>
> Q: What is a stack?
> A: LIFO data structure. Push to add, pop to remove. Like a stack of plates — you take from the top.
>
> Q: What is Big-O notation?

### Output

Q: What is Big-O notation?

A: Big-O notation describes how the running time or memory usage of an algorithm grows as the input size increases. Think of it like predicting traffic on a road—the more vehicles you add, the more congestion you expect. For example, a linear search checks elements one by one, giving O(n), while binary search cuts the search space in half each time, giving O(log n).

Self Score: 4/5

---

## Pattern 3 – Chain of Thought

### Prompt

"Explain Big-O notation to a placement interview candidate. Think step by step before answering. Step 1: define Big-O in one sentence. Step 2: give one concrete example with code. Step 3: explain why interviewers ask about it. Step 4: synthesise into a 3-sentence summary."

### Output

Good instinct bringing this up — you're looking at a **prompt engineering** technique called **chain-of-thought prompting**. Let me break down exactly what this prompt is doing and why it works.

---

**What this prompt is doing**

It's not just asking _what_ to explain — it's telling the model _how to think_ before it answers. That's the key move.

The four steps force a specific cognitive path:

**Step 1** — "Define in one sentence" prevents the model from rambling into a vague multi-paragraph opener. Constraint = precision.

**Step 2** — "Concrete example with code" anchors the abstract to something real. Without this, models tend to stay theoretical.

**Step 3** — "Why interviewers ask about it" shifts perspective from _what_ to _so what_. This is the part most students miss entirely.

**Step 4** — "Synthesise into 3 sentences" forces compression. A model that understood everything should be able to compress it — if it can't, it didn't really understand it.

---

**Why this technique works**

Large language models generate text token by token. When you force intermediate reasoning steps _before_ the final answer, the model's earlier output becomes context for its later output — so the final answer is literally built on better intermediate thinking. This is why "think step by step" measurably improves accuracy on reasoning tasks, not just output quality.

---

**The three prompt engineering levers this uses**

| Lever                 | How it's used here                                                       |
| --------------------- | ------------------------------------------------------------------------ |
| **Structure**         | Numbered steps impose an order the model can't skip                      |
| **Constraint**        | "one sentence", "3-sentence summary" — length limits force clarity       |
| **Perspective shift** | Step 3 asks the model to reason _about the audience_, not just the topic |

---

**How you can steal this pattern for your prep**

You can use the same structure to self-test before interviews. Instead of asking "what is dynamic programming?", ask yourself:

> _Step 1: Define it in one sentence. Step 2: Give one example with code. Step 3: Why would an interviewer ask this? Step 4: Summarise in 3 sentences._

If you can't complete all four steps cleanly, that's exactly where your understanding has a gap. It's a much sharper diagnostic than just re-reading notes.

---

The prompt you shared is a solid template. Want me to rewrite it for 2-3 other common interview topics — like recursion, hashmaps, or OS concepts — so you have ready-made study prompts for your prep?

Self Score: 5/5

---

## Pattern 4 – Structured Output

### Prompt

> "Explain Big-O notation for a placement interview. Return ONLY valid JSON with this exact shape — no markdown fences, no commentary:
>
> {
> "definition": "one-sentence definition",
> "intuition": "concrete analogy",
> "code_example": "Python snippet showing O(n) and O(n²)",
> "common_pitfall": "what students get wrong",
> "interview_test_question": "a follow-up question an interviewer might ask"
> }"

### Output

{
"definition": "Big-O notation describes the upper bound of an algorithm's growth rate — how the number of operations scales as input size n approaches infinity.",
"intuition": "Imagine searching for a name in a phone book. Flipping page by page is O(n) — more pages, proportionally more work. Opening to the middle and halving the search each time is O(log n). Big-O is the label on that strategy, not the stopwatch.",
"code_example": "def linear_search(arr, target):\n for x in arr: # O(n) — one pass\n if x == target:\n return True\n return False\n\ndef has_duplicate(arr):\n for i in range(len(arr)): # O(n²) — nested loops\n for j in range(i+1, len(arr)):\n if arr[i] == arr[j]:\n return True\n return False",
"common_pitfall": "Students count loops but forget that the operation inside the loop matters too — calling .sort() inside a loop turns O(n) into O(n² log n) without a single extra loop in sight.",
"interview_test_question": "Your solution runs in O(n²) — how would you optimise it, and what data structure would you reach for first?"
}

Self Score: 4/5

---

## Pattern 5 – System Prompt

### User Prompt

Explain Big-O notation.

### Output

Big-O notation tells us how an algorithm's performance changes as the input size grows. For example:

```python
for num in arr:
    print(num)
```

This loop runs n times, so it's O(n). Interviewers ask Big-O questions to check whether you can write scalable and efficient solutions, not just working code.

Self Score: 4/5

---

## Pattern 6 – Prompt Chaining

### Conversation 1 Output

1. Definition of Big-O
2. Common Time Complexities
3. Comparing Algorithms
4. Time vs Space Complexity
5. Interview Importance

### Conversation 2 Output

Definition of Big-O:
Big-O notation measures how an algorithm's resource usage grows with input size.

Common Time Complexities:
Students should know O(1), O(log n), O(n), O(n log n), and O(n²).

Comparing Algorithms:
Big-O allows comparison between multiple solutions to identify the most scalable approach.

Time vs Space Complexity:
Time complexity measures execution steps, while space complexity measures memory consumption.

Interview Importance:
Companies ask Big-O questions to assess analytical thinking and optimization skills.

### Conversation 3 Final Output

Big-O notation helps measure how an algorithm's performance changes as input size grows. You should know common complexities such as O(1), O(log n), O(n), O(n log n), and O(n²). It helps compare multiple solutions and choose the most scalable one. Remember that efficiency involves both time and memory usage. Interviewers ask Big-O questions to evaluate optimization and problem-solving skills.

Practice Question:
What is the time complexity of binary search, and why?

Self Score: 5/5

---

# Peer Scores

| Pattern           | Clarity | Context | Specificity | Format | Verification | Total |
| ----------------- | ------- | ------- | ----------- | ------ | ------------ | ----- |
| Persona           | 2       | 2       | 2           | 2      | 1            | 9/10  |
| Few-Shot          | 2       | 1       | 2           | 2      | 1            | 8/10  |
| Chain-of-Thought  | 2       | 2       | 2           | 2      | 1            | 9/10  |
| Structured Output | 2       | 2       | 2           | 2      | 1            | 9/10  |
| System Prompt     | 2       | 2       | 2           | 1      | 1            | 8/10  |
| Prompt Chaining   | 2       | 2       | 2           | 2      | 2            | 10/10 |

---

# Reflection

For my placement-prep students, the patterns I will use most are Persona and Prompt Chaining.

Persona helps generate explanations tailored specifically to engineering students preparing for interviews. The explanations become more relevant, practical, and easier to understand.

Prompt Chaining produces the highest-quality content because the task is broken into smaller focused steps. First, important concepts are identified, then expanded, and finally summarized into a concise explanation. This approach consistently produces more complete and accurate interview-preparation material.
