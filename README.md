```
def generate_candidates(dataset, k):
    candidates = defaultdict(int)
    for sequence in dataset:
        for itemset in combinations(sequence, k):
            candidates[itemset] += 1
    return candidates

# Function to perform GSP algorithm
def gsp(dataset, min_support):
    # Initialize frequent patterns dictionary
    frequent_patterns = defaultdict(int)
    k = 1
    while True:
        candidates = generate_candidates(dataset, k)
        # Prune candidates with support less than min_support
        candidates = {pattern: support for pattern, support in candidates.items() if support >= min_support}
        if not candidates:
            break
        frequent_patterns.update(candidates)
        k += 1
    return frequent_patterns
```
