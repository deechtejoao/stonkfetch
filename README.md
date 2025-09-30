# stonkfetch

A command-line tool that fetches and displays stock information with beautiful colored ASCII art logos, inspired by neofetch.

## Description

stonkfetch is a Python-based CLI utility that retrieves real-time stock market data from Yahoo Finance and displays it alongside a company logo rendered as ASCII art. The tool features colored ASCII logos (when PIL/Pillow is available), customizable display options, and comprehensive stock information including price, volume, market cap, and 52-week ranges.

## Features

- **Real-time stock data** from Yahoo Finance API
- **Colored ASCII art logos** of company logos (requires PIL/Pillow)
- **Automatic logo fetching** from Clearbit and UpLead APIs
- **Comprehensive stock information** including:
  - Current price and change percentage
  - Open, high, low prices
  - Trading volume
  - Market capitalization
  - 52-week high/low
  - Last update timestamp
- **Customizable display options** for colors and ASCII art width
- **Fallback ASCII art** when logos are unavailable or PIL is not installed
- **Built-in domain mapping** for 50+ popular stock symbols

## Requirements

- Python 3.6+
- PIL/Pillow (optional, for colored ASCII art logos)

## Installation

1. Clone or download the `stonkfetch` script
2. Make it executable:
   ```bash
   chmod +x stonkfetch
   ```
3. (Optional) Install PIL/Pillow for colored ASCII art:
   ```bash
   pip install Pillow
   ```
4. (Optional) Move to a directory in your PATH:
   ```bash
   sudo mv stonkfetch /usr/local/bin/
   ```

## Usage

### Basic Usage

```bash
./stonkfetch AAPL
```

### Command-Line Options

```bash
./stonkfetch <symbol> [options]
```

**Arguments:**
- `symbol` - Stock ticker symbol (e.g., AAPL, TSLA, MSFT)

**Options:**
- `--no-color` - Disable all colored output (ASCII and text)
- `--no-color-ascii` - Disable colors in ASCII art only (keep text colors)
- `--no-logo` - Disable logo fetching and use fallback ASCII art
- `--ascii-width <width>` - Width of ASCII art in characters (default: 40)
- `--version` - Show version information
- `-h, --help` - Show help message

### Examples

```bash
# Display Apple stock with colored logo
./stonkfetch AAPL

# Display Tesla with grayscale ASCII art
./stonkfetch TSLA --no-color-ascii

# Display Microsoft without logo (use fallback)
./stonkfetch MSFT --no-logo

# Display Google with custom ASCII width
./stonkfetch GOOGL --ascii-width 50

# Display Amazon with no colors at all
./stonkfetch AMZN --no-color
```

## How It Works

### Data Flow

1. Fetches stock data from Yahoo Finance API
2. Retrieves company logo from Clearbit or UpLead APIs
3. Converts logo to colored ASCII art (if PIL is available)
4. Formats and displays stock information alongside the ASCII art

### Supported Stock Symbols

The tool includes built-in domain mappings for 50+ popular stocks including:
- Tech: AAPL, MSFT, GOOGL, AMZN, META, TSLA, NVDA, AMD, INTC
- Finance: JPM, V, MA, PYPL, COIN
- Consumer: WMT, DIS, NKE, SBUX, MCD
- Cloud/SaaS: CRM, NOW, SNOW, DDOG, NET

For symbols not in the mapping, the tool attempts to derive the domain from the company name.

## Output Format

The display shows:
- Company logo as colored ASCII art (left side)
- Stock symbol and exchange (top right)
- Stock information in a formatted list (right side):
  - Company name
  - Current price with currency
  - Price change (amount and percentage)
  - Daily open, high, low
  - Trading volume
  - Market capitalization
  - 52-week high/low
  - Last update timestamp

## Dependencies

### Required
- Python standard library modules:
  - `argparse` - Command-line argument parsing
  - `json` - JSON data parsing
  - `urllib.request` - HTTP requests
  - `datetime` - Timestamp formatting
  - `typing` - Type hints
  - `sys` - System operations
  - `re` - Regular expressions

### Optional
- `PIL` (Pillow) - For colored ASCII art generation
  - Without PIL, the tool uses simple fallback ASCII art

## Error Handling

The tool handles various error scenarios:
- Invalid stock symbols
- Network connectivity issues
- API request failures
- Missing PIL/Pillow library
- Malformed API responses

## License
MIT
