
# Trie (Prefix Tree)

A Trie (pronounced "try") — also called a prefix tree — is a tree-like data structure used to store a dynamic set of strings where keys are usually strings. The structure is optimized for retrieval of keys by prefix and makes many string operations (insert, search, prefix search) efficient.

**Why use a Trie:**
- **Prefix queries:** fast retrieval of all keys sharing a common prefix.
- **Predictive text / autocomplete:** efficient suggestion lookups.
- **Dictionary and spell-check:** quick membership tests and near-match operations.

**Core concepts**
- **Node:** each node represents a character (or part of a key). A node holds:
	- children: mapping from character -> child node (array, hash map, or fixed-size vector for alphabet).
	- is_end (or terminal flag): marks whether a path from root to this node forms a complete key.
	- (optional) value / count / frequency: extra data per word or to support advanced queries.
- **Root:** an empty node representing the start of every key.
- **Path:** characters along edges from root to node form the prefix or full key.

**Basic operations**
- **Insert(key):** walk from root following characters of key, creating child nodes where missing; set `is_end` at final node.
- **Search(key):** walk following characters; if traversal completes and final node's `is_end` is true, key exists.
- **StartsWith(prefix):** walk prefix; if traversal succeeds, at least one key has that prefix.
- **Delete(key):** unset `is_end`; optionally prune nodes that become unnecessary (no children and not `is_end`).

Complexities (assuming alphabet size sigma, key length m):
- Insert: O(m)
- Search: O(m)
- StartsWith: O(p) for prefix length p
- Space: O(n * average_key_length * factor) — tries can be memory-hungry; implementations trade memory for speed.

**Implementation notes & variations**
- **Children representation:**
	- Hash map / dictionary: flexible, good for large alphabets.
	- Fixed array (size = alphabet): very fast, memory-heavy (good for small fixed alphabets like lowercase a-z).
	- Compressed/Patricia Trie: compresses chains of single-child nodes to save space.
- **Case / normalization:** normalize keys (lowercase, remove punctuation) before insert/search.
- **Storing values:** Tries can store complete values (not just presence) at `is_end` nodes for map-like behavior.
- **Suffix trie / generalized trie:** store all suffixes to solve substring problems; much larger but powerful for text algorithms.

**Common use-cases**
- Autocomplete and typeahead engines
- IP routing (longest prefix match) — specialized variants
- Spell-checkers, dictionary lookups, word games
- Efficient multi-pattern matching when combined with Aho–Corasick automaton

**How to Master Tries**
1. **Understand the structure:** implement a basic Trie in a language of your choice and test insert/search/prefix.
2. **Visualize:** draw node diagrams for strings inserted (e.g., "car", "cat", "cap"). Visual tools or a small print function help.
3. **Practice problems:** solve problems that rely on Tries — autocomplete, longest common prefix, counting unique prefixes, word squares, and prefix-based grouping.
4. **Implement variations:** build a compressed (Patricia) Trie, a suffix Trie, and try Aho–Corasick for multiple-pattern search.
5. **Optimize memory:** experiment with arrays vs maps, bit-packing, and node pooling. Measure memory/time trade-offs.
6. **Complex algorithms:** learn Aho–Corasick, suffix automata, and how tries relate to suffix arrays for advanced string algorithms.
7. **Interview prep:** practice explaining node layout, runtime/space trade-offs, and coding `insert`/`search`/`delete` live.

**Common pitfalls**
- Not normalizing input (case, whitespace) before insertion/search.
- Forgetting to set or check `is_end`, causing false positives for prefixes.
- Failing to manage memory for large alphabets — sudden TLE or OOM in production.

**Exercises (progressively harder)**
1. Implement `Trie` with `insert`, `search`, and `startsWith`.
2. Add a `delete` method that prunes unused nodes.
3. Count how many stored words share a given prefix.
4. Return all words with a given prefix (implement DFS from prefix node).
5. Implement a compressed Trie (merge single-child chains).
6. Build Aho–Corasick automaton from a list of patterns and run multi-pattern search on a text.

**Recommended resources**
- CLRS: sections on string algorithms (for context and complexity)
- Articles and tutorials on Patricia tries and Aho–Corasick
- Practice sites: LeetCode problems tagged `trie`, HackerRank string challenges

**Next steps I can do for you**
- add a language-specific example implementation (Python/C++/Java/JS)
- add unit tests and small example runner
- add visualizer script to print trie structure

---
Updated README.md for Trie concepts, operations, variations, and a mastery path.

