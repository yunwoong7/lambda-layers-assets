# aws-idp-assets

## 1. **custom_layer_common.zip**

This package includes common dependencies used across multiple Lambda functions.

## 2. **custom_layer_lambda.zip**

This package includes Lambda-specific dependencies.

## 3. **custom_layer_lambda_pandas.zip**

This package includes Pandas and related dependencies for data processing in Lambda.

## Folder Structure Example

```
aws-idp-assets/
├── custom_layer_common.zip
├── custom_layer_lambda.zip
└── custom_layer_lambda_pandas.zip
```

## Usage Example

To use these layers in your AWS Lambda function, specify the ARN of the layer in your function configuration.

```bash
aws lambda update-function-configuration \
    --function-name my-function \
    --layers arn:aws:lambda:region:account-id:layer:custom_layer_common:version \
             arn:aws:lambda:region:account-id:layer:custom_layer_lambda:version
```

Replace `region`, `account-id`, and `version` with your specific values.

# AWS Lambda Layers

This directory contains pre-built **AWS Lambda layer ZIP packages** used for intelligent document processing, hybrid search, and AI-based analysis workloads.  
Each ZIP file bundles a specific set of Python dependencies optimized for serverless execution with AWS Bedrock, OpenSearch, and LangChain-based agents.

---

## 1. **custom_layer_common.zip**

**Description:**  
General-purpose utility layer that combines AWS SDK and document/image processing libraries for common Lambda functions.

**Requirements:**  
```
boto3 opensearch-py pillow PyMuPDF PyPDF2
```

**Includes:**  
- `boto3` – AWS SDK for interacting with S3, DynamoDB, and Bedrock  
- `opensearch-py` – OpenSearch Python client  
- `Pillow` – image manipulation  
- `PyMuPDF`, `PyPDF2` – PDF parsing and text extraction

**Use Cases:**  
- General Lambda utilities  
- Document preprocessing and uploading  
- Bedrock + OpenSearch integration workflows

---

## 2. **custom_layer_image_processing.zip**

**Description:**  
Image and PDF preprocessing layer for visual document analysis and content extraction.

**Requirements:**  
```
pillow PyMuPDF PyPDF2
```

**Includes:**  
- `Pillow` – image handling (resize, format conversion)  
- `PyMuPDF` – efficient PDF page rendering and text extraction  
- `PyPDF2` – structure parsing and metadata operations

**Use Cases:**  
- PDF and image preprocessing before LLM analysis  
- OCR-ready document conversion  
- Blueprint or scanned document visualization

---

## 3. **custom_layer_opensearch.zip**

**Description:**  
Lightweight layer providing the OpenSearch Python SDK for indexing and search queries.

**Requirements:**  
```
opensearch-py
```

**Includes:**  
- `opensearch-py` – official OpenSearch client for indexing, bulk upload, and query operations

**Use Cases:**  
- Lambda-based search pipelines  
- Hybrid keyword/vector search  
- Metadata indexing for retrieval workflows

---

## 4. **custom_layer_analysis_package.zip**

**Description:**  
Full-featured analysis layer that enables multi-agent reasoning, search orchestration, and Bedrock integration.

**Requirements:**  
```
langchain_aws langchain_core langgraph pydantic aws_xray_sdk opensearch-py pillow
```

**Includes:**  
- `langchain_aws`, `langchain_core`, `langgraph` – LLM orchestration and workflow management  
- `pydantic` – structured model validation  
- `aws_xray_sdk` – AWS X-Ray tracing for observability  
- `opensearch-py` – search integration  
- `Pillow` – lightweight image operations

**Use Cases:**  
- Intelligent Document Processing (IDP) Agents  
- Multi-agent coordination via LangGraph  
- AI-powered reasoning and search augmentation

---

## Folder Structure

```
aws-idp-assets/
├── custom_layer_common.zip
├── custom_layer_image_processing.zip
├── custom_layer_opensearch.zip
├── custom_layer_analysis_package.zip
└── README.md
```

---