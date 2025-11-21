# ER_splitting

Documenting lit review on splitting logic for Entity Resolution

## Overview

This repository contains comprehensive D2 documentation for entity resolution splitting logic. The documentation provides visual representations of various splitting strategies, architectural patterns, and practical examples used in entity resolution systems.

## D2 Documentation Files

### 1. `entity_resolution_splitting.d2`

Main documentation covering:
- **Entity Resolution Overview**: Complete workflow from data input to resolved entities
- **Splitting Strategies**: Size-based, memory-based, hash-based, and semantic splitting approaches
- **Parallel Processing Architecture**: Distributed processing with master-worker patterns
- **Blocking and Splitting Interaction**: How blocking keys influence splitting decisions
- **Load Balancing**: Techniques for balanced workload distribution
- **Adaptive Splitting Algorithm**: Dynamic algorithms for optimal partition sizing
- **Data Skew Handling**: Strategies to handle imbalanced data distributions
- **Performance Metrics**: Key metrics for evaluating splitting quality
- **Common Splitting Patterns**: Round-robin, range-based, random, and hierarchical patterns
- **Best Practices**: Guidelines for effective entity resolution splitting

### 2. `splitting_examples.d2`

Practical examples including:
- **Customer Database Deduplication**: 100K records with phonetic and geographic blocking
- **Academic Publication Matching**: 1M publications using hash-based splitting
- **E-commerce Product Catalog**: 5M products with adaptive two-tier splitting for skewed data
- **Real-time Stream Processing**: Windowed micro-batch splitting for streaming data
- **Strategy Comparison**: Detailed comparison of different splitting approaches
- **Performance Scaling**: Recommendations for different dataset sizes
- **Error Handling**: Recovery strategies for common failure scenarios
- **Implementation Tips**: Practical recommendations for production systems

## Viewing the Documentation

To view and render the D2 diagrams, you have several options:

### Option 1: Install D2 CLI (Recommended)

```bash
# On macOS with Homebrew
brew install d2

# On Linux
curl -fsSL https://d2lang.com/install.sh | sh -s --

# On Windows
scoop install d2
```

Then render the diagrams:

```bash
# Render to SVG (scalable)
d2 entity_resolution_splitting.d2 entity_resolution_splitting.svg
d2 splitting_examples.d2 splitting_examples.svg

# Render to PNG
d2 entity_resolution_splitting.d2 entity_resolution_splitting.png
d2 splitting_examples.d2 splitting_examples.png

# Render to PDF
d2 entity_resolution_splitting.d2 entity_resolution_splitting.pdf
d2 splitting_examples.d2 splitting_examples.pdf
```

### Option 2: Use D2 Playground

Visit [D2 Playground](https://play.d2lang.com/) and paste the contents of the `.d2` files to view them interactively in your browser.

### Option 3: Use VS Code Extension

Install the [D2 extension](https://marketplace.visualstudio.com/items?itemName=terrastruct.d2) for Visual Studio Code to preview diagrams directly in your editor.

## Key Concepts

### Entity Resolution (ER)

Entity Resolution is the process of identifying records that refer to the same real-world entity across one or more datasets. It's also known as:
- Record linkage
- Deduplication
- Entity matching
- Fuzzy matching

### Splitting Logic

Splitting logic is crucial for scaling entity resolution to large datasets. It involves:

1. **Partitioning**: Dividing the dataset into manageable chunks
2. **Distribution**: Assigning chunks to processing units
3. **Load Balancing**: Ensuring even workload distribution
4. **Result Aggregation**: Combining results from parallel processing

### Why Splitting Matters

- **Scalability**: Process millions/billions of records
- **Performance**: Reduce computation time through parallelization
- **Memory Efficiency**: Work within memory constraints
- **Cost Optimization**: Better resource utilization

## Contributing

Contributions to improve or extend the documentation are welcome. When adding new diagrams or examples:

1. Follow the existing D2 syntax and style conventions
2. Use meaningful labels and descriptions
3. Apply appropriate colors for visual clarity
4. Include practical context and use cases
5. Test rendering before committing

## References

- [D2 Documentation](https://d2lang.com/)
- [D2 Language Specification](https://d2lang.com/tour/intro)

## License

This documentation is provided for educational and reference purposes.
