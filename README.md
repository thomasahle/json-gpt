# JSON GPT

A fast and cheap JSON generation library for GPT models.
Json-gpt uses OpenAI's streaming API and passes tokens directly into a [Lark parser](https://github.com/lark-parser/lark) which catches errors as soon as they appear, so they can be corrected.
Lark grammars are also available for other output formats, such as python code.

## Demo

Let's see json-gpt in action, struggling with a dodgy json schema:

https://github.com/thomasahle/json-gpt/assets/946355/2eb56138-b48e-4d8d-8441-c4dfae0625c7

## Features

- json-gpt is built using Lark, so you can modify the grammar to any CFG, such as Python code.
- json-gpt uses streaming, so you don't have to completely restart your generation upon an error, like some retry-based libraries.
- json-gpt uses an adaptive rollback, which prevents some weird errors in other constrained generation frameworks based on token maksing.

## Installation

To install json-gpt, you will need Python 3.6 or higher. Clone this repository and install the required dependencies:

```bash
git clone https://github.com/thomasahle/json-gpt.git
cd json-gpt
pip install lark openai
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
Publication Year: 1925
Tags: fiction, classic

Title: "Murder on the Orient Express"
Author: Agatha Christie
Publication Year: 1934
Tags: fiction, mystery

Title: "A Brief History of Time"
Author: Stephen Hawking
Publication Year: 1988
Tags: non-fiction, science

Let's write this list of books using the following JSON schema:

{
  books: [
    {
      title: string,
      author: string,
      publicationYear: integer,
      tags: [string],
    }
  ]
}

json ="""

print(prompt, end="")
output = generate_content(prompt, demo_mode=True, verbose=True)
print("\nFinal output: json =", output)
```

## Configuration

You can configure the following parameters:

- `model`: The ID of the model to use for generation.
- `max_tokens`: The maximum number of tokens to generate.
- `temperature`: Controls randomness in generation, lower is more deterministic.
- `verbose`: Enable verbose mode to get more information during generation.

## Acknowledgements

- [Outlines](https://github.com/outlines-dev/outlines): A much more general constrained generation library.
- [Lark](https://github.com/lark-parser/lark): A simple parser library in python.
