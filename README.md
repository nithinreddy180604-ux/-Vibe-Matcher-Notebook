# Vibe Matcher: Fashion Recommendation System

A lightweight vibe-based recommendation system that matches user queries with fashion products using semantic similarity. Built with Python and Jupyter notebooks, this prototype demonstrates AI-powered personalization for fashion discovery.

## Overview

This project implements a vibe-based recommendation engine that:
- Takes natural language vibe queries (e.g., "energetic urban chic")
- Embeds product descriptions using OpenAI embeddings (with TF-IDF fallback)
- Returns top-3 product matches via cosine similarity
- Includes evaluation metrics and latency profiling

## Features

- **Semantic Search**: Uses OpenAI embeddings (`text-embedding-ada-002` or `text-embedding-3-small`) for semantic understanding
- **Fallback Support**: Gracefully falls back to TF-IDF when OpenAI API is unavailable
- **Edge Case Handling**: Implements fallback strategies for low similarity scores
- **Performance Monitoring**: Includes latency profiling and evaluation metrics
- **Evaluation Framework**: Tests multiple queries and measures recommendation quality

## Dataset

The system includes a curated catalog of 10 fashion products with:
- Product names and descriptions
- Vibe tags (e.g., "boho", "urban", "minimal", "sustainable")
- Categories spanning dresses, jackets, sweaters, denim, athleisure, boots, skirts, parkas, tops, and joggers

## Installation

### Requirements
- Python 3.10+
- Jupyter Notebook or JupyterLab

### Dependencies
```bash
pip install openai pandas numpy scikit-learn matplotlib
```

### Optional: OpenAI API Key
Set your OpenAI API key for embeddings:
```python
import os
os.environ['OPENAI_API_KEY'] = 'sk-...'
```

## Usage

1. **Run the Notebook**: Open `vibe_matcher.ipynb` in Jupyter
2. **Set API Key**: Configure OpenAI API key (optional, falls back to TF-IDF)
3. **Execute Cells**: Run all cells to see the recommendation system in action
4. **Test Queries**: Try different vibe queries like:
   - "energetic urban chic"
   - "cozy loungewear" 
   - "minimal sustainable"

## How It Works

### 1. Data Preparation
- Creates a product catalog with descriptions and vibe tags
- Structures data for efficient similarity computation

### 2. Embedding Generation
- **Primary**: OpenAI embeddings for semantic understanding
- **Fallback**: TF-IDF vectorization when API unavailable
- **Latency Tracking**: Measures embedding generation time

### 3. Similarity Matching
- Computes cosine similarity between query and product embeddings
- Returns top-3 matches with similarity scores
- Handles edge cases with fallback strategies

### 4. Evaluation
- Tests multiple queries across different vibe categories
- Measures recommendation quality (similarity threshold: 0.7)
- Profiles latency performance
- Provides visualizations of results

## Performance Metrics

The system tracks:
- **Good Rate**: Percentage of recommendations above similarity threshold (0.7)
- **Average Top-1 Score**: Mean similarity score of best match
- **Latency**: Query processing time in seconds
- **Model Usage**: Tracks whether OpenAI or TF-IDF was used

## Architecture

```
Query → Embedding → Similarity Computation → Top-K Results → Evaluation
  ↓         ↓              ↓                    ↓            ↓
Text    OpenAI/TF-IDF   Cosine Similarity   Ranking    Metrics/Plots
```

## Future Improvements

- **Vector Database**: Integrate Pinecone or FAISS for scalable search
- **Rich Embeddings**: Combine name, description, and vibe tags
- **Query Expansion**: Add synonym expansion and diversification
- **Caching**: Cache embeddings for faster repeated queries
- **Reranking**: Add cross-encoder reranker for precision
- **Dynamic Thresholds**: Implement adaptive similarity thresholds
- **Vibe Taxonomy**: Create structured vibe mapping system

## Files

- `vibe_matcher.ipynb` - Main notebook with implementation
- `vibe_matcher_executed.ipynb` - Executed version with outputs
- `vibe_matcher_executed.html` - HTML export for sharing

## License

This project is part of Nexora's AI research and development initiatives.

## Contributing

This is a prototype system. For production use, consider:
- Implementing proper error handling and logging
- Adding comprehensive testing
- Setting up monitoring and alerting
- Creating proper API endpoints
- Adding user feedback loops for continuous improvement