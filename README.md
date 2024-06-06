# OECD.AI - Policy Analyzer
(Credits and Original Author(s): [Hack4Good 2023](https://www.analytics-club.org/hack4good) and [OECD.ORG](https://www.oecd.org/switzerland/))
<br> [Disclaimer and Absolute Rights](https://github.com/omphcompany/oecdpolicyanalysis/blob/main/disclaimer.txt)

[^1]: Saad-Falcon, J., Barrow, J., Siu, A., Nenkova, A., Yoon, D. S., Rossi, R. A., & Dernoncourt, F. (2023). [*PDFTriage: Question Answering over Long, Structured Documents*](https://arxiv.org/abs/2309.08872). arXiv preprint arXiv:2309.08872

## Original Design Approach: 
* GUI via Streamlit
* Extracts semi-structured PDF into structured text using [Adobe PDF Extract API](https://developer.adobe.com/document-services/docs/overview/pdf-extract-api/)
* Uses PDFTriage[^1] style prompting (similar to ReAct) to answer questions about the documents.
* Answers to questions provide the section where they were found in the document.

## New Design & Approach: OECD AI Policy Analyzer Using LLMs

This repository presents a significant enhancement to the original OECD AI Policy Analyzer tool.  Moving beyond basic content extraction with the Adobe PDF Extract API, this version leverages Large Language Model (LLM)-based content analysis and structuring to align with the specific requirements and objectives of academic research.

## Key Enhancements:

## LLM-Powered Content Analysis:

### Deep Understanding: 
Utilizes advanced natural language processing capabilities of LLMs to understand the nuances, context, and subtleties within AI policy documents.

### Structured Representation: 
Transforms unstructured policy text into structured formats, facilitating systematic analysis and comparison.

### Qualitative and Mixed-Methods: 
Enables researchers to employ qualitative or mixed-methods approaches to analyze the content, drawing upon established scholarly works and data analysis techniques.

### Academic Research Focus:

### Tailored to Research Objectives: 
Allows customization of analysis parameters and research questions to align with specific academic research goals.

### Comparative Analysis: 
Facilitates in-depth comparison of national AI strategies, agendas, and action plans across different countries, as reported on OECD.AI.

### Pattern and Trend Identification: 
Employs LLM capabilities to identify patterns, trends, and emerging themes within AI policy documents, aiding in the development of new research insights.
Integration with OECD.AI:

### Data Source: 
Leverages the comprehensive collection of AI policy documents available on the OECD.AI platform.

### Policy Landscape Analysis: 
Provides a powerful tool for analyzing the global AI policy landscape and understanding the diverse approaches taken by different nations.

## How it Works:

* Data Input: Utilizes policy documents directly from OECD.AI.
* LLM-based Analysis: Applies LLM models to perform content analysis, structuring, and extraction of relevant information.
* Research Framework Integration: Allows users to apply qualitative or mixed-methods research frameworks to analyze the structured data.
* Comparative Analysis: Enables comparison of AI policies across countries, identifying similarities, differences, and best practices.
* Results: Generates comprehensive reports, visualizations, and exportable data to support academic research and policy analysis.

## Disclaimer:

This enhanced tool is a research prototype designed to support academic inquiry. While it leverages advanced LLM technology, users should exercise critical judgment when interpreting results and consider the tool as a complement to, not a replacement for, rigorous scholarly analysis.

### Note:

This enhanced OECD AI Policy Analyzer tool serves as a valuable resource for researchers, policymakers, and stakeholders engaged in the study of AI governance. By integrating LLM-powered analysis with academic research methodologies, it empowers users to explore the complexities of AI policy in greater depth and contribute to the development of evidence-based policy recommendations.

## GUI Quickstart

Environment variables need to be set in order to run the interactive GUI.
Create an `.env` file in the root of the repo (you can use `cp .env.default .env`) with the following variables:

| Environment Variable | Description |
| --- | --- |
| `ADOBE_CLIENT_ID` | Create Adobe Developer account and select "Get credentials" [here](https://developer.adobe.com/document-services/docs/overview/pdf-extract-api/) |
| `ADOBE_CLIENT_SECRET` | Copy from "Get credentials" [here](https://developer.adobe.com/document-services/docs/overview/pdf-extract-api/) as with `ADOBE_CLIENT_ID` |
| `OPENAI_API_KEY` | Get the [OpenAI API key](https://help.openai.com/en/articles/4936850-where-do-i-find-my-api-key) |

After setting the environment variables (make sure to to **not** enclose the env variables in quotes), you can run the code in one of two ways:

<details>
<summary><b><font size="+1">Conda Environment</font></b></summary>

1. Create a [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) environment with the required dependencies:

To **create** a conda environment after cloning the repo:
```
# from the root of the repo
conda env create -f environment.yml
# to activate the environment
conda activate hack4good
# to deactivate the environment (when you're done)
conda deactivate
```

(Optional) To **update** the conda environment after pulling latest changes:
```
conda activate hack4good
conda env update -f environment.yml --prune
```

(Optional) To **remove** the conda environment:
```
conda deactivate
conda env remove -n hack4good
```

2. Run the streamlit app
```
python -m streamlit run app/main.py
```

3. Access the streamlit app at [http://localhost:8501](http://localhost:8501)
</details>

<details>
<summary><b><font size="+1">Docker</font></b></summary>

1. Run (or build) the [Docker](https://docs.docker.com/get-docker/) image

To **run** the latest docker image:
```
docker run -p 8501:8501 --env-file .env --volume $PWD/data:/app/app/data ghcr.io/dvdblk/hack4good-oecd/app:latest
```

(Optional) To **build** the docker image locally (after cloning the repo) and run it:
```
docker build -t hack4good .
docker run -p 8501:8501 --env-file .env --volume $PWD/data:/app/app/data hack4good
```

2. Access the streamlit app at [http://localhost:8501](http://localhost:8501)

</details>

## Contributing
1. Install [pre-commit](https://pre-commit.com/#installation).
2. Run `pre-commit install` to apply the repo's pre-commit hooks to your local git repo.
3. Add your changes, commit and create a pull request with `main` branch as the target.
