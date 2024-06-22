# Password-generator Version 1.0

# Password Generator Utility Manual

## Overview
This utility generates passwords according to a given template and supports a CLI interface. It can work in PIPE and supports logging for detailed processing information (`-vvv`).

## Features

### Generation Based on Character Sets
1. **Random Method:** 
   - Generates a password of a specified length from a set of characters.
2. **Pattern-Based Generation:** 
   - Generates passwords that follow specific rules or conditions.

### Defining a Character Set
- Define the character set directly in the command line argument.
- Optionally add commonly used character ranges.
- Manually specify characters using the `\S` option.

### Supported Characters
- All Unicode characters in the ranges [U+0001, U+D7FF] and [U+E000, U+FFFF] are supported, except { U+0009 / '\t', U+000A / '\n', U+000D / '\r' }.
- Characters in the range [U+010000, U+10FFFF] are not supported.

### Pattern-Based Generation
Create passwords using the following placeholders:

| Placeholder | Type              | Character Set                                    |
|-------------|-------------------|--------------------------------------------------|
| `d`         | Digit             | `0123456789`                                     |
| `l`         | Lower-Case Letter | `abcdefghijklmnopqrstuvwxyz`                    |
| `L`         | Mixed-Case Letter | `ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz` |
| `u`         | Upper-Case Letter | `ABCDEFGHIJKLMNOPQRSTUVWXYZ`                    |
| `p`         | Punctuation       | `,.;:`                                           |
| `\`         | Escape            | Use following character as is                    |
| `{n}`       | Repeat            | Repeat the previous placeholder `n` times        |
| `[...]`     | Custom Char Set   | Define a custom character set                    |

### Examples of Patterns
- `dddd` generates passwords like: `41922`, `12733`, `43960`, `07660`, `12390`, `74680`, ...
- `u{4}d{3}\-l{2}` generates passwords like: `DHRF345-st`, `FHGFds4-vt`, `DERS774-sd`

## Command Line Interface

### Commands
- `-n`: Set length of password and generate a random password from the set {small letter ASCII, big letter ASCII, digit}
- `-t`: Set template for generating passwords
- `-f`: Get a list of patterns from a file and generate random passwords for each
- `-c`: Specify the number of passwords to generate
- `-vvv`: Enable verbose mode (`-v`, `-vv`, `-vvv`)
- `-h`: Display help information
- `-S`: Define character set

### Output
- The output can be redirected using pipe.

## References

1. **Command Line Interface:**
   - [argparse module](https://docs.python.org/3/library/argparse.html) — Parser for command-line options, arguments, and sub-commands
   - [How to Build Command Line Interfaces in Python With argparse](https://realpython.com/command-line-interfaces-python-argparse/#setting-the-action-to-be-taken-for-an1-argument)

2. **Logging in Python:**
   - [Logging HOWTO](https://docs.python.org/3/howto/logging.html)
   - [Advanced Logging Tutorial](https://docs.python.org/3/howto/logging.html#logging-advanced-tutorial)
   - [Logging Cookbook](https://docs.python.org/3/howto/logging-cookbook.html)
   - [logging.config — Logging configuration](https://docs.python.org/3/library/logging.config.html)
   - [logging.handlers — Logging handlers](https://docs.python.org/3/library/logging.handlers.html)
   - [Python Logging Guide – Best Practices and Hands-on Examples](https://coralogix.com/log-analytics-blog/python-logging-best-practices-tips)
   - [How to collect, customize, and centralize Python logs](https://www.datadoghq.com/blog/python-logging-best-practices/)
