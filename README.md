# LLM-Ready Metadata Generator

Welcome to the **LLM-Ready Metadata Generator**! This project provides developers, researchers, and enthusiasts with a simple and effective way to make their repositories machine-readable for Large Language Models (LLMs). By following our method, you can create structured metadata that enhances your repository's discoverability, usability, and value when consumed by AI systems.

---

## Why This Matters

Large Language Models are increasingly used to analyze and process code repositories. However, the lack of standardized metadata often makes it challenging for LLMs to understand and summarize a project's structure, purpose, and key features. With the **LLM-Ready Metadata Generator**, you can:

- **Boost AI Integration**: Provide LLMs with well-structured data that they can easily parse and interpret.
- **Improve Automation**: Enable seamless automation for tasks like dependency analysis, feature identification, and API usage extraction.
- **Enhance Discoverability**: Help your repository stand out by making it AI-friendly for indexing and summarization systems.

---

## How It Works

1. **Run the Meta-Prompt**  
   Use the meta-prompt provided below on your repository to generate a machine-readable file located at `/metadata/llm_readme.jso`. The meta-prompt is specifically designed to analyze your codebase and output structured metadata in JSON format.

2. **Validate the Output**  
   Ensure the generated `llm_readme.jso` is accurate and aligns with your project structure. Use any JSON validator to confirm the syntax.

3. **Integrate It Into Your Repository**  
   Commit the file to your repository under the `/metadata` directory.

4. **Share Your Repository**  
   Once the metadata is in place, share your repository with the world! LLMs and other AI systems will now have an easier time understanding your work.

---

## Meta-Prompt

Below is the meta-prompt to generate the metadata file:

```plaintext
You are an advanced language model that has read and analyzed the provided code repository. Your goal is to produce a structured metadata file in JSON format that summarizes the repository for machine consumption. Specifically:

1. The output **must** be a single JSON object.
2. The output **must** be saved as a single file located at `/metadata/llm_readme.jso` (intentionally `.jso` extension).
3. The structure of the JSON object should follow this template:

{
  "project_name": "string",
  "project_description": "string",
  "architecture": {
    "...": "..."
  },
  "features": [
    "string",
    "string"
  ],
  "key_files": {
    "string": "description",
    "string": "description"
  },
  "configuration": [
    {
      "variable": "string",
      "default": "string",
      "purpose": "string"
    },
    ...
  ],
  "api_endpoints": [
    {
      "method": "string",
      "path": "string",
      "description": "string"
    },
    ...
  ],
  "license": "string or object"
}

4. **Focus** on producing only structured metadata — no additional text or commentary outside the JSON object.
5. Ensure the JSON is valid and properly escaped if necessary.
6. If any sections do not apply, either omit them or provide an empty array/object.

Using the repository’s files, codebase, or any provided documentation, fill out these sections as completely and accurately as possible. The result will be consumed by downstream LLMs or automated scripts for analysis.
```
# Benefits

## For Developers
* **Save Time**: Automate repository documentation in a format ideal for AI analysis.
* **Improve Clarity**: Provide structured data that highlights your project's key aspects.
* **Encourage Contributions**: Help potential contributors quickly understand your repository.

## For AI Researchers
* **Standardize Metadata**: Build datasets with consistent, high-quality project metadata.
* **Optimize Parsing**: Reduce errors in LLM summarization and analysis pipelines.

## For Teams
* **Simplify Onboarding**: Make it easy for new team members or stakeholders to grasp your project.
* **Facilitate Communication**: Provide a clear and concise overview of your repository for presentations or discussions.

## Example Usage

Here's an example of how your `llm_readme.json` might look:

```json
{
  "project_name": "LLM-Ready Metadata Generator",
  "project_description": "A utility to create machine-readable repository metadata for Large Language Models (LLMs).",
  "architecture": {
    "server": "Handles HTTP routes and API requests.",
    "database": "Stores metadata and project details in a structured format.",
    "llm_integration": "Provides hooks for AI systems to parse metadata."
  },
  "features": [
    "Structured metadata generation",
    "Optimized for AI consumption",
    "Supports standard JSON output"
  ],
  "key_files": {
    "main.py": "Entry point for the application",
    "utils.py": "Utility functions for data processing"
  },
  "configuration": [
    {
      "variable": "METADATA_PATH",
      "default": "/metadata",
      "purpose": "Location where the metadata file is stored"
    }
  ],
  "license": "MIT"
}
```

## How to Contribute

We welcome contributions from everyone! Here's how you can help:

1. **Fork the repository** and clone it locally.
2. **Run the meta-prompt** on your project to test its effectiveness.
3. **Submit improvements** to the meta-prompt or add templates for different use cases.
4. **Share your feedback** by opening an issue or joining the discussion.

## License

This project is licensed under the MIT License. Feel free to use it, modify it, and distribute it as needed.

**Let's make repositories more accessible for AI together!** If you've successfully generated your `llm_readme.json`, share it with the community and show others how to get started.

## Save Your Codebase with CodexGigantus

CodexGigantus is a powerful command-line tool written in Go that processes files in a specified directory based on given criteria. It's designed to integrate seamlessly with Language Learning Models (LLMs) for extracting smaller code components.

### Features
* Specify root directory
* Ignore specific directories
* Exclude files with specific extensions
* Include only files with specific extensions
* Process and display contents of text files

### Installation

#### Prerequisites
* Go 1.16 or later

#### Steps
1. Clone the repository:
```bash
git clone https://github.com/baditaflorin/codexgigantus.git
```

2. Navigate to the project directory:
```bash
cd codexgigantus
```

3. Build the project:
```bash
./build.sh
```

### Usage

#### Basic Command
```bash
./codexgigantus -dir /path/to/dir --ignore-dir logs,temp --ignore-ext log,tmp --include-ext txt,md
```

#### How to test it on this repo
```bash
./CodexGigantus -dir . --ignore-file CodexGigantus,.DS_Store,qodana.yaml --ignore-ext txt --ignore-dir .git,.idea --save --output-file chatgpt_code.txt
```

### Flags Explanation
* `--dir` or `-dir`: Comma-separated list of directories to search (default: current directory)
* `--ignore-file` or `-ignore-file`: Comma-separated list of files to ignore
* `--ignore-dir` or `-ignore-dir`: Comma-separated list of directories to ignore
* `--ignore-ext` or `-ignore-ext`: Comma-separated list of file extensions to ignore
* `--include-ext` or `-include-ext`: Comma-separated list of file extensions to include
* `--ignore-suffix` or `-ignore-suffix`: Comma-separated list of file suffixes to ignore
* `--recursive` or `-recursive`: Recursively search directories (default: true)
* `--debug` or `-debug`: Enable debug output
* `--save`: Save the output to a file
* `--output-file`: Specify the output file name (default: output.txt)
* `--show-size`: Show the size of the result in bytes
* `--show-funcs`: Show only functions and their parameters

### Internal Use Examples

#### Frontend
```bash
codexgigantus -dir social-network-frontend -ignore-file package-lock.json -ignore-dir node_modules,__previewjs__ -ignore-ext svg,png,ico,md -output-file frontend.txt -save
```

#### Backend
```bash
codexgigantus -dir social-network-backend -ignore-file package-lock.json,auth_test.go -ignore-dir tests -ignore-ext sum,mod -output-file backend.txt -save
```

#### Debugging
```bash
codexgigantus -debug -dir . -ignore-file package-lock.json,codexgigantus,frontend.txt -ignore-dir cmd,pkg,.idea,.git,node_modules,__previewjs__ -ignore-ext svg,png,ico,md -output-file frontend.txt -save
```

### Development Notes
* Configuration Parsing: The ParseFlags function in config.go handles all command-line arguments
* File Processing: The ProcessFiles function in file_processor.go handles directory traversal and file filtering
* Functional Style: The code uses functional programming principles for better modularity and testability
* Debug Information: Use the -debug flag to enable detailed debug output
* Utility Functions: Common utility functions are consolidated in utils.go

### Testing
The code is organized for easy unit testing. Each function handles a single responsibility, and functional parameters can be mocked during tests. To ensure the code is easy to test, functional parameters are used for gathering and processing files, allowing easy mocking during tests. Each function handles a single responsibility, making the codebase modular and maintainable.

### Contributing
Contributions are welcome! Please submit a pull request or open an issue to discuss any changes.

### License
This project is licensed under the MIT License.

**Let's make repositories more accessible for AI together!** If you've successfully generated your `llm_readme.json`, share it with the community and show others how to get started.
