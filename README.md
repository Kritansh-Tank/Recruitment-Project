# AI-Powered Recruitment System

An intelligent recruitment automation system built with CrewAI that streamlines the hiring process by automatically parsing job descriptions, analyzing resumes, matching candidates, and generating personalized outreach emails.

## 🚀 Features

- **Automated Job Description Parsing**: Extracts key requirements, skills, and qualifications from job descriptions
- **Resume Analysis**: Parses candidate resumes (PDF/DOCX) and extracts structured information
- **Intelligent Skill Matching**: Calculates compatibility scores between candidates and job requirements
- **Personalized Email Generation**: Creates customized outreach emails for qualified candidates
- **Multi-format Support**: Handles both PDF and DOCX file formats
- **Sentiment Analysis**: Ensures positive and engaging communication tone

## 🏗️ Architecture

The system is built using CrewAI framework with four specialized AI agents:

### 1. Job Description Parser Agent
- **Role**: Analyzes job descriptions and extracts key information
- **Output**: Structured JSON with required skills, experience levels, and responsibilities

### 2. Resume Parser Agent
- **Role**: Extracts detailed candidate information from resumes
- **Output**: JSON with candidate name, skills, experience, education, and contact details

### 3. Skill Matcher Agent
- **Role**: Compares candidate profiles with job requirements
- **Output**: Compatibility score (0-1) indicating job fit

### 4. Candidate Outreach Agent
- **Role**: Generates personalized recruitment emails
- **Output**: Professional email drafts with interview scheduling

## 📋 Prerequisites

- Python 3.8+
- OpenAI API Key
- Serper API Key (for web search capabilities)

## 🛠️ Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd recruitment-project
   ```

2. **Install required packages**:
   The notebook includes an automatic package installer. Run the first cell to install:
   - `openai>=1.0.0`
   - `crewai>=0.28.0`
   - `crewai-tools>=0.4.0`
   - `langchain-openai>=0.1.0`
   - `pydantic>=2.0.0`
   - `PyPDF2`
   - `python-docx`

3. **Set up API keys**:
   Update the API keys in the notebook:
   ```python
   os.environ["OPENAI_API_KEY"] = "your-openai-api-key"
   os.environ["SERPER_API_KEY"] = "your-serper-api-key"
   ```

## 🚀 Usage

### Running the Jupyter Notebook

1. **Open the notebook**:
   ```bash
   jupyter notebook recruitment_project.ipynb
   ```

2. **Execute cells sequentially**:
   - Cell 1: Install required packages
   - Cell 2: Import warnings and suppress them
   - Cell 3: Configure environment variables and API keys
   - Cell 4: Import CrewAI components and initialize LLM
   - Cell 5: Set up custom tools
   - Cell 6: Define AI agents
   - Cell 7: Create tasks for each agent
   - Cell 8: Define file reading functions
   - Cell 9: Initialize crew and run the main process

3. **Provide input files**:
   When prompted, enter:
   - Path to job description file (PDF or DOCX)
   - Paths to candidate resume files (comma-separated)

### Input File Formats

- **Job Description**: PDF or DOCX file containing the job posting
- **Resumes**: PDF or DOCX files containing candidate information

### Output

The system generates:

#### Selected Candidates (Compatibility Score ≥ 0.7)
- Candidate name
- Compatibility score
- Personalized email draft

#### Unselected Candidates (Compatibility Score < 0.7)
- Candidate name
- Compatibility score

## 📊 Example Output

```
Selected Candidates

Candidate: John Doe
Compatibility Score: 0.85
Email Draft: Dear John Doe,

We are excited to reach out to you regarding the Software Engineer position at TechCorp...

Unselected Candidates

Candidate: Jane Smith
Compatibility Score: 0.45
```

## 🔧 Configuration

### Compatibility Threshold
The default threshold for candidate selection is 0.7. You can modify this in the main execution code:

```python
if compatibility_score >= 0.7:  # Adjust threshold as needed
    selected_candidates.append(result_dict)
```

### Email Template Customization
The outreach emails include:
- Candidate's name
- Job description details
- Company information
- Interview slot (scheduled for March 2025)
- Personalized message highlighting relevant skills

### Memory and Storage Settings
The system is configured to disable CrewAI memory to avoid storage issues:
```python
os.environ["CREWAI_STORAGE_DIR"] = ""
os.environ["DISABLE_CREWAI_MEMORY"] = "true"
```

## 🛡️ Error Handling

- **File Format Validation**: Supports only PDF and DOCX formats
- **JSON Parsing**: Handles malformed JSON responses gracefully
- **API Error Management**: Includes retry logic and error reporting
- **Input Validation**: Validates file paths and content

## 🔍 Troubleshooting

### Common Issues

1. **API Key Errors**:
   - Ensure OpenAI and Serper API keys are valid and have sufficient credits
   - Check API key format and permissions

2. **File Reading Issues**:
   - Verify file paths are correct
   - Ensure files are not corrupted or password-protected
   - Check file permissions

3. **Memory Errors**:
   - The system disables CrewAI memory by default
   - If issues persist, restart the kernel

4. **Package Installation**:
   - Run the first cell to install all required packages
   - Use `!pip install package-name` for individual installations

## 📈 Performance Optimization

- Uses GPT-4o-mini for cost-effective processing
- Parallel processing capability for multiple resumes
- Optimized file reading for large documents
- Efficient JSON parsing and error handling