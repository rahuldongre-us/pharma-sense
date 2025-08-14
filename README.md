# 💊 PharmaSense: Semantic Search with AWS S3 Vectors

This project demonstrates a scalable **semantic search pipeline** for structured Medicaid drug data using **Amazon S3 Vectors**. We encode drug records into dense vector embeddings using a custom PyTorch model, store them in S3 Vectors with metadata, and perform similarity search using free-text queries like `"diabetes treatment"`.

### About AWS S3 Vectors

Amazon S3 Vectors is a new feature from AWS that allows you to store and query vector embeddings directly in Amazon S3. This capability is designed to support AI workloads, particularly those involving semantic search, retrieval-augmented generation (RAG), and recommendations, by providing a cost-effective and scalable solution for managing large volumes of vector data. Amazon S3 Vectors is a purpose-built, cost‑optimized vector storage feature within Amazon S3, enabling native storage and querying of vector embeddings at scale with up to 90% cost savings versus standalone vector databases.


- **Elasticity & Durability**: Leverages S3’s architecture for scalable vector storage
- **Cost Efficiency**: Up to 90% savings on vector storage and querying
- **Performance**: Provides sub-second similarity searches with strong read-after-write consistency
- **Vector Indexing**: Supports up to 10,000 indexes per bucket, each can hold tens of millions of vectors
- **Metadata Support**: Attach filterable and non-filterable metadata for advanced filtering
- **API & CLI Options**: Use Boto3 SDK (PutVectors, QueryVectors, etc.) or the s3vectors-embed-cli
- **AWS Integrations**: Native support with Amazon Bedrock Knowledge Bases, SageMaker Unified Studio, and OpenSearch

---

## 📌 Use Case

Semantic search over structured drug reimbursement records:
- Match drugs similar to a text query (e.g. condition, treatment)
- Filter by metadata (e.g. US state, year)
- Power intelligent search, RAG, or insight extraction in healthcare

---

## 🧠 Key Features

| Feature                         | Description                                       |
|--------------------------------|---------------------------------------------------|
| 🧬 Custom embedding model       | Encodes categorical & numeric drug data to vectors |
| 🗃️ S3 Vectors indexing         | Stores 32D embeddings using native AWS service     |
| 🧵 Metadata support             | Search by `state`, `drugname`, `year`, etc.        |
| 🔎 Text-to-vector querying      | Sentence transformer encodes user text             |
| 📊 Scalable and extensible     | Works with millions of embeddings                  |

---

## 🧪 Demo Notebook

➡ [`semantic-search.ipynb`](notebooks/semantic-search.ipynb)

### 🧬 Pipeline:

1. **Load Medicaid drug data**  
2. **Encode each record** into a 32D semantic vector using PyTorch
3. **Upload vectors** to Amazon S3 with metadata (`state`, `year`, `drugname`)
4. **Use a sentence transformer** to encode a text query
5. **Query AWS S3 Vectors** for the top K similar drugs
6. **Display matches**, distance scores, and associated metadata

---

## ⚙️ Setup Instructions

### ✅ Requirements

- Python 3.10+
- AWS credentials with access to S3 Vectors (in preview)
- Region: `us-east-1` or another supported one

### 📦 Install dependencies

```
%pip install pandas numpy torch boto3 sentence-transformers
```

### 🚀 Run the Notebook

```
jupyter notebook notebooks/semantic-search.ipynb
```

### 🔍 Example Query
```
input_text = "diabetes treatment"
```

### Top result:
```
Match key: drug-vector-4199
Distance: 0.7495
Metadata: {'year': 2022, 'state': 'SC', 'drugname': 'HUMULIN N'}
```

## 🛠️ Technologies Used

AWS S3 Vectors (preview) for vector storage and querying

PyTorch for custom embedding model

Sentence Transformers (MiniLM) for text input encoding

Boto3 for AWS SDK integration

## 📈 Future Improvements

Add a UI with Streamlit or Gradio

Embed via Amazon Bedrock or OpenAI

Index clinical notes, trial reports, or PubMed abstracts

Enable retrieval-augmented generation (RAG) with text + metadata


## 🙋‍♂️ Author

Rahul Dongre, 
GitHub: @rahuldongre-us