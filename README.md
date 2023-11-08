# JSON GPT

Welcome to JSON GPT – a library designed to leverage the power of GPT models for generating correct JSON structures efficiently. This tool harnesses the OpenAI's streaming API and directly feeds the output to a robust CFG parser built with Lark, ensuring high performance and accuracy.

## Features

- **GPT-based JSON Generation**: Utilize GPT models to generate JSON code that adheres to specified grammar.
- **Streaming API Integration**: Take advantage of OpenAI's streaming API for efficient and faster JSON generation.
- **Lark Parser Validation**: Incorporate Lark's parsing capabilities to validate and correct JSON output in real-time.
- **Demo Mode**: Optionally introduce errors for demonstration purposes, showcasing the error correction capability.
- **Customization**: Adjust parsing and generation settings such as maximum token length, temperature, and verbosity.

## Installation

To install JSON GPT, you will need Python 3.6 or higher. Clone this repository and install the required dependencies:

```bash
git clone https://github.com/your-username/JSON-GPT.git
cd JSON-GPT
pip install -r requirements.txt
```

## Usage

Before you begin, make sure to set your OpenAI API key as an environment variable:

```bash
export OPENAI_KEY='your-api-key'
```

To use JSON GPT, import the library and call the `generate_content` function with your JSON schema prompt:

```python
import openai
from json_gpt import generate_content

# Set your OpenAI API key
openai.api_key = os.getenv("OPENAI_KEY")

# Your JSON schema prompt
prompt = """
Title: "The Great Gatsby"
Author: F. Scott Fitzgerald
...
"""

# Generate JSON content
output = generate_content(prompt)
print(output)
```

## Configuration

You can configure the following parameters:

- `model`: The ID of the model to use for generation.
- `max_tokens`: The maximum number of tokens to generate.
- `temperature`: Controls randomness in generation, lower is more deterministic.
- `verbose`: Enable verbose mode to get more information during generation.

## Contributions

Contributions are welcome! Please read the [CONTRIBUTING.md](CONTRIBUTING.md) file for details on our code of conduct, and the process for submitting pull requests to us.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

## Acknowledgments

- OpenAI for providing the GPT models and API.
- Lark parser, which powers the backbone of JSON validation.

Happy Coding!
