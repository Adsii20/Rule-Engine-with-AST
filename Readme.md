# Rule Engine Application 
A comprehensive business rules management system featuring a Flask-based REST API, a Tkinter GUI, and an automated test suite. This system enables creating, combining, evaluating, and modifying business rules using Abstract Syntax Trees (AST) through multiple interfaces.
# System Components
# 1. Rule Engine API (app.py)

- Flask-based REST API
- SQLite database backend
- AST-based rule parsing and evaluation
- JSON response format

# 2. Rule Engine GUI (rlg.py)

- Tkinter-based desktop application
- User-friendly interface
- Real-time response display
- Error handling and validation

# 3. Test Suite (test.py)

- Automated testing script
- Example rule scenarios
- API endpoint verification
- Integration testing capabilities

# Features

- Create complex business rules using AND/OR logic
- Combine multiple rules with logical operators
- Evaluate data against stored rules
- Modify existing rules
- Persistent storage using SQLite
- Visual interface for rule management
- Automated testing suite
- AST-based rule parsing and evaluation

# Prerequisites

- Python 3.6+
- Required packages:
```
Copyflask
sqlalchemy
requests
tkinter (usually comes with Python)
```
- SQLite database

# Installation

1. Clone the repository:
```
git clone <repository-url>
cd rule-engine-system
```
2. Create and activate a virtual environment:
```
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```
3. Install dependencies:
```
pip install -r requirements.txt
```
# Running the System

1. Start the API server:
```
python app.py
```
2. Launch the GUI (optional):
```
python rlg.py
```
3. Run tests (optional):
```
python test.py
```
# Rule Format
Rules use the following syntax:
```
<field> <operator> <value> [AND|OR] <field> <operator> <value>
```
Operators:

- Comparison: >, <, =
- Logical: AND, OR
- Grouping: ( )

Examples:
```
age > 18
income > 50000
(age > 18 AND income > 50000) OR status = 'premium'
```
# Usage Examples
# 1. Using the API Directly
```
import requests
# Create a rule
response = requests.post("http://localhost:5000/create_rule", 
    json={"rule_string": "age > 30 AND department = 'Sales'"})

# Evaluate a rule
response = requests.post("http://localhost:5000/evaluate_rule",
    json={
        "rule_id": 1,
        "data": {"age": 35, "department": "Sales"}
    })
```
# 2. Using the GUI

1. Create Rule:

- Enter rule string: age > 30 AND department = 'Sales'
- Click "Create Rule"


2. Evaluate Rule:

- Enter Rule ID: 1
- Enter data: {"age": 35, "department": "Sales"}
- Click "Evaluate Rule"


# 3. Running Tests
```
python test.py
```
Sample test output:
```
Testing create_rule...
Response: {"id": 1, "ast": {...}}

Testing combine_rules...
Response: {"id": 3, "combined_ast": {...}}

Testing evaluate_rule...
Response: {"result": true}
```
# API Endpoints
# 1. Create Rule

- POST /create_rule
- Body: {"rule_string": "age > 18"}

# 2. Combine Rules

- POST /combine_rules
- Body: {"rule_ids": [1, 2]}

# 3. Evaluate Rule

- POST /evaluate_rule
- Body: {"rule_id": 1, "data": {"age": 25}}

# 4. Modify Rule

- POST /modify_rule
- Body: {"rule_id": 1, "new_rule_string": "age > 21"}

# Project Structure
```
rule-engine-system/
├── app.py            # API server
├── rlg.py           # GUI application
├── test.py          # Test suite
├── rules.db         # SQLite database
├── README.md        # Documentation
└── requirements.txt # Dependencies
```
# Testing
The test suite (test.py) provides:

1. Individual endpoint testing
2. Complex rule creation and evaluation
3. Rule combination testing
4. Rule modification verification

To add new tests:

1. Open test.py
2. Add test functions
3. Update main test sequence

# Error Handling
The system handles:

- Network errors
- Invalid JSON
- Rule syntax errors
- Database errors
- API response errors
- Invalid rule IDs

# Development Guidelines

1. API Development:

- Follow RESTful principles
- Add comprehensive error handling
- Include logging
- Document new endpoints


2. GUI Development:

- Maintain consistent UI
- Add input validation
- Handle all error cases
- Update documentation


3. Test Development:

- Add test cases for new features
- Maintain test coverage
- Document test scenarios
- Include edge cases


# Security Considerations
For production:

- Enable authentication
- Add input validation
- Enable HTTPS
- Configure CORS
- Implement rate limiting
- Secure the database
- Add proper logging

# Common Issues and Solutions

1. Connection Errors

- Check if API server is running
- Verify BASE_URL configuration
- Check network connectivity


2. Database Issues

- Check SQLite file permissions
- Verify database path
- Ensure proper table creation


3. Rule Evaluation Failures

- Validate rule syntax
- Check JSON data format
- Verify rule ID exists


# Contributing

1. Fork the repository
2. Create a feature branch
3. Add tests for new features
4. Submit pull request

# Future Enhancements

- Rule templates
- Rule versioning
- Batch processing
- Advanced visualization
- User authentication
- Performance metrics
- API documentation UI

# Acknowledgments

- Flask framework
- SQLAlchemy ORM
- Tkinter GUI library
- Python community
