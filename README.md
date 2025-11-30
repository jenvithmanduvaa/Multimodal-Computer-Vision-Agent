# Multimodal Computer Vision Agent (Vision-Tool Loop) 🖼️🧠

A sophisticated **Multimodal AI Agent** built on **LangGraph** capable of analyzing images, processing visual information, and executing multi-step reasoning that requires both textual and visual analysis.

## 📌 Project Overview
This project demonstrates an agent capable of complex, iterative problem-solving for image-based queries. The agent can process questions like "Identify all objects in this image and calculate the ratio of the largest to the smallest" by cyclically calling vision tools and reasoning about the results.

**Key Objectives:**
- Implement a **Tool-Calling Loop** that allows the agent to execute actions (tools) and receive feedback until the query is fully answered.
- Integrate a **Vision Language Model (VLM)** as a callable tool for image analysis.
- Manage the dynamic **State** needed for multimodal inputs (image path, tool output, conversation history).

## 🏗️ Architecture & Features
The core feature is a **cyclic graph** that facilitates iterative reasoning:

-   **Agent Node:** The central hub where the LLM reasons on the user's input and decides whether to respond directly or call a tool.
-   **Tool Node:** A node dedicated to running the actual image processing or analysis function (e.g., calling the VLM for object detection).
-   **Cyclic Edge:** An edge that directs the flow back from the **Tool Node** to the **Agent Node**, enabling the agent to evaluate the tool's output and determine if further steps or different tools are required.
-   **Multimodal Tool:** An integrated vision model capable of consuming images and returning structured observations (e.g., bounding boxes, object labels).

## 🛠️ Tech Stack
-   **Framework:** LangGraph
-   **Language:** Python
-   **Libraries:** LangChain (Tools), Vision Language Models (VLM), Langfuse
-   **Concepts:** Tool-Tool Looping, Multimodal Reasoning, State Management

## 🚀 Usage Example
The agent answers a complex visual query:

1. **Input:** "What is the largest object in this photo, and what color is it?" (with an image attached).
2. **Agent Node:** LLM determines it needs visual information and calls the **Object Detection Tool**.
3. **Tool Node:** The tool processes the image, returning a list of objects and their properties.
4. **Cyclic Edge:** Flow returns to the **Agent Node**.
5. **Agent Node:** The LLM reads the tool output, identifies the largest object based on area/size metric, and extracts its color.
6. **Final Output:** "The largest object is a red fire truck."
