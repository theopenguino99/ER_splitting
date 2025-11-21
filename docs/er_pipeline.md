# Schema 

```d2 layout="elk"

# Direction: right
direction: right

# Data Sources
ds1: Data Source 1
ds2: Data Source 2
ds3: Data Source 3

# Preprocessing
preprocessing: Preprocessing {
  shape: process
  style.fill: "#f0f0f0"
}
ds1 -> preprocessing
ds2 -> preprocessing
ds3 -> preprocessing

# Blocking
blocking: Blocking {
  shape: process
  style.fill: "#e0e0ff"

  sb: Standard Blocking
  sn: Sorted Neighborhood
  qg: Q-grams Blocking
}
preprocessing -> blocking

# Matching
matching: Matching {
  shape: process
  style.fill: "#e0ffe0"

  em: Exact Match
  pm: Phonetic Match (e.g., Soundex)
  dm: Distance Match (e.g., Levenshtein)
  ml: ML-based Match
}
blocking -> matching

# Clustering
clustering: Clustering {
  shape: process
  style.fill: "#ffffe0"
}
matching -> clustering

# Resolved Entities
resolved: Resolved Entities {
  shape: database
  style.fill: "#d0f0d0"
}
clustering -> resolved
```
