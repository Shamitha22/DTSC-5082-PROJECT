# DTSC-5082-PROJECT
Agentic Multimodal Medical Assistant

DTSC 5082 – Final Project

Overview

The Agentic Multimodal Medical Assistant is a system designed to retrieve and analyze medical information using both images and text. The goal of the project is to build a functional prototype that demonstrates how modern embedding models, vector search, and agent-style logic can work together to support medical image understanding and case comparison.

The notebook downloads a publicly available medical image dataset, preprocesses thousands of images, generates embeddings for both the images and their corresponding captions, and indexes them for fast similarity retrieval. Users can search the collection using a text description, an image, or a combination of both, and the system returns the most relevant images along with their captions.

Project Objectives
	1.	Build a multimodal pipeline capable of processing large collections of medical images.
	2.	Extract meaningful embeddings from both text and images.
	3.	Construct an efficient vector search index using FAISS.
	4.	Implement a retrieval system that supports text-to-image, image-to-image, and hybrid search.
	5.	Demonstrate agent-like behavior by allowing the system to choose the appropriate search path based on the type of user input.

Dataset

The project uses a subset of the PMC medical image dataset hosted on Zenodo. The notebook automatically downloads and extracts the dataset. Captions and labels are loaded from a separate file, which provides descriptive information for each image.

Dataset contents include:
	•	Medical scans and diagnostic images
	•	Accompanying text captions and labels
	•	Approximately one hundred folders, each containing multiple images

Methodology

1. Data Loading

The notebook imports the medical image dataset, scans directories for valid image formats, and loads the corresponding captions from a CSV file. Basic checks ensure that missing or corrupted files are skipped without interrupting execution.

2. Preprocessing

Images are standardized using the Pillow library. Captions undergo text cleaning to remove unnecessary characters. The result is a consistent dataset ready for embedding generation.

3. Embedding Models

Two types of embeddings are created:
	•	Text embeddings generated using a Sentence-BERT model
	•	Image embeddings generated using a Vision Transformer (CLIP-based architecture)

Both embeddings are normalized so that similarity comparisons are meaningful and stable.

4. Vector Index Construction

A FAISS index is built to store all image embeddings. This allows high-speed similarity queries, even with large numbers of images. Once the embeddings are indexed, the system can locate the closest matches for any given query in a fraction of a second.

5. Retrieval System

The assistant supports three modes of retrieval:
	•	Text query: users enter a caption or description, and the system returns the most relevant medical images.
	•	Image query: users provide an image to find visually similar cases.
	•	Combined query: users can supply both an image and text, and the system interprets both inputs.

The notebook displays the retrieved images using Matplotlib, allowing users to visually inspect the results.

6. Agentic Behavior

The project incorporates simple agentic logic. When a user submits a query, the system determines whether the input is an image, text, or a combination of both. Based on this decision, the appropriate embedding model and search path are automatically selected.

Technologies Used
	•	Python
	•	Pandas and NumPy
	•	SentenceTransformers
	•	HuggingFace Transformers
	•	Torch and TorchVision
	•	Pillow
	•	FAISS (CPU version)
	•	Matplotlib

How to Run the Project
	1.	Open the notebook in Google Colab.
	2.	Upload the captions CSV file into the same working directory.
	3.	Run all cells from top to bottom. The dataset will download automatically.
	4.	Use the final section of the notebook to perform text or image searches.
	5.	Retrieved images will be displayed directly in the notebook.

Results

The final system is able to retrieve medical images that closely match either textual descriptions or example images provided by the user. The combination of vision transformers, text transformers, and vector search results in a flexible and efficient retrieval tool. Although this project is a prototype, it demonstrates how multimodal models and agent-style decision mechanisms can be used to support medical research and diagnostic review.
