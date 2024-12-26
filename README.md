# AI-Powered Finance Agent

A Python-based bookkeeping system that leverages OpenAI's GPT model to intelligently categorize transactions. This application combines traditional bookkeeping functionality with AI-powered categorization for more accurate expense tracking.

## Features

- AI-powered transaction categorization using OpenAI's GPT model
- Add income and expense transactions
- Generate detailed financial reports
- Track running balance
- Simple command-line interface
- Automatic date tracking for all transactions

## Prerequisites

- Python 3.6 or higher
- OpenAI API key
- `openai` Python package

## Installation

1. Clone this repository:
```bash
git clone https://github.com/jobonano/ai-finance-agent
cd ai-finance-agent
```

2. Install required dependencies:
```bash
pip install openai
```

3. Set up your OpenAI API key:
   - Sign up for an OpenAI account at https://openai.com
   - Generate an API key from your OpenAI dashboard
   - Replace the empty string in `openai.api_key = ""` with your API key

## Configuration

The application uses OpenAI's `text-davinci-003` model for categorization. You can modify these parameters in the `get_expense_category` function:
```python
response = openai.Completion.create(
    engine="text-davinci-003",
    prompt=prompt,
    max_tokens=10,
    temperature=0.7
)
```

## Usage

Run the program:
```bash
python bookkeeping.py
```

The program offers three main options:
1. Add transaction
2. View report
3. Exit

### Adding Transactions

When adding a transaction:
- Enter a positive amount for income
- Enter a negative amount for expenses
- Provide a description for AI-based categorization

Example:
```python
Select an option (1/2/3): 1
Enter amount (positive for income, negative for expense): -25.50
Enter description of the transaction: lunch at downtown cafe
```

### AI Categorization

The system uses OpenAI's GPT model to categorize expenses into:
- Office Supplies
- Entertainment
- Food
- Utilities
- Transport
- Other

The AI analyzes the transaction description to determine the most appropriate category.

### Viewing Reports

Reports include:
- Total income
- Total expenses
- Current balance
- Detailed transaction list with dates, descriptions, AI-assigned categories, and amounts

Example report output:
```
--- Bookkeeping Report ---
Total Income: $1000.00
Total Expenses: $350.00
Balance: $650.00

Transactions:
2024-12-26 - salary deposit - Other - $1000.00 - income
2024-12-26 - lunch at downtown cafe - Food - $-25.50 - expense
```

## Code Structure

- `get_expense_category()`: Uses OpenAI API to categorize transactions
- `add_transaction()`: Records new transactions with AI-assigned categories
- `generate_report()`: Creates financial summary and transaction list
- `print_report()`: Displays formatted report
- `main()`: Handles user interaction and program flow

## Data Structure

Each transaction is stored with the following structure:
```python
{
    "amount": float,
    "description": str,
    "category": str,  # AI-assigned category
    "type": str,      # "expense" or "income"
    "date": str
}
```

## API Usage Considerations

- The application makes API calls to OpenAI for each transaction categorization
- Be mindful of API usage limits and costs
- Consider implementing caching for repeated similar transactions
- Monitor your OpenAI API usage through their dashboard

## Future Improvements

Potential enhancements could include:
- Persistent storage (database or file-based)
- Batch categorization to optimize API usage
- Custom category training for the AI model
- Category confidence scores
- Historical transaction analysis
- API usage monitoring and optimization
- Export capabilities (CSV, PDF)
- Web interface

## Security Notes

- Never commit your OpenAI API key to version control
- Consider using environment variables for API key management
- Implement proper error handling for API failures
- Monitor and log API responses for security

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. Areas of particular interest:
- API error handling improvements
- Category optimization
- Security enhancements
- Testing suite development
