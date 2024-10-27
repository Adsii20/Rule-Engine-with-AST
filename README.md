# Rule Engine Application 
This project implements a 3-tier rule engine application using Flask, SQLAlchemy, and SQLite. It allows users to create, combine, and evaluate rules based on Abstract Syntax Trees(ASTs). The application provides a backend API and a Tkinter-basedfrontend for creating and managing rules.

## Table of Contents:
* Features
* Setup
* Components
* API
* Endpoints
* Usage
* Example
* Testing
* License

### Features:

Create Rule: Define rules with logical
conditions, which generate unique IDs and are represented in AST format.
Combine Rules: Merge multiple rules into a single rule with a unique ID
and a combined AST. Evaluate Rule: Test data against rules to determine
if they satisfy the specified conditions. Modify Rule: Update existing
rules by modifying the rule string. Setup Install the required
dependencies:

bash Copy code pip install flask sqlalchemy Run the Flask application:

bash Copy code python main.py Components Backend: main.py (Flask,
SQLAlchemy, SQLite) Frontend: rlg.py (Tkinter UI) Automated Test Script:
test.py (tests the app using the requests library) Application
Features 1. Create Rule Creates a rule and displays its ID in the UI.
For example, creating two rules will result in two rules with IDs 1 and
2.

2.  Combine Rule Combines multiple rules using comma-separated rule IDs
    to create a "mega rule" with a unique ID displayed in the Tkinter
    UI.

3.  Evaluate Rule Uses a rule ID and JSON data to evaluate the rule
    conditions against the provided parameters.

API Endpoints Create Rule URL: /create_rule Method: POST Data Params:
JSON { "rule_string": "(age \> 30 AND department = 'Sales') OR (salary
\> 50000)" } Success Response: JSON { "id": 1, "ast": "..." } Combine
Rules URL: /combine_rules Method: POST Data Params: JSON { "rule_ids":
\[1, 2\] } Success Response: JSON { "id": 3, "combined_ast": "..." }
Evaluate Rule URL: /evaluate_rule Method: POST Data Params: JSON {
"rule_id": 3, "data": { "age": 35, "department": "Sales", "salary":
60000, "experience": 6 } } Success Response: JSON { "result": true }
Modify Rule URL: /modify_rule Method: POST Data Params: JSON {
"rule_id": 1, "new_rule_string": "age \> 40 AND department = 'HR'" }
Success Response: JSON { "message": "Rule updated successfully" } Usage
Example Here's a step-by-step workflow using curl commands to test the
rule engine:

Create the First Rule:

bash Copy code curl -X POST http://127.0.0.1:5000/create_rule -H
"Content-Type: application/json" -d '{"rule_string": "(age \> 30 AND
department = 'Sales') OR (salary \> 50000)"}' Create the Second Rule:

bash Copy code curl -X POST http://127.0.0.1:5000/create_rule -H
"Content-Type: application/json" -d '{"rule_string": "experience \> 5
AND department = 'Marketing'"}' Combine the Rules:

bash Copy code curl -X POST http://127.0.0.1:5000/combine_rules -H
"Content-Type: application/json" -d '{"rule_ids": \[1, 2\]}' Evaluate
the Combined Rule:

bash Copy code curl -X POST http://127.0.0.1:5000/evaluate_rule -H
"Content-Type: application/json" -d '{ "rule_id": 3, "data": { "age":
35, "department": "Sales", "salary": 60000, "experience": 6 } }' Modify
a Rule:

bash Copy code curl -X POST http://127.0.0.1:5000/modify_rule -H
"Content-Type: application/json" -d '{ "rule_id": 1, "new_rule_string":
"age \> 40 AND department = 'HR'" }' Testing Use the test.py script to
automate testing of the rule engine's functionality:

bash Copy code python test.py This script tests:

Creating rules Combining rules Evaluating rules Modifying rules License
This project is licensed under the MIT License.

This README should cover the setup, usage, and testing of your
application effectively. Let me know if there are any specific sections
you'd like to expand!
