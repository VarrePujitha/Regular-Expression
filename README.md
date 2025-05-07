# Regular-Expression
User Input Validation Script

This Python script collects and validates user inputs for Name, Date of Birth, Email ID, and Mobile Number using regular expressions (`re` module). Each field is validated against a specific pattern, and the program continues to prompt the user until valid input is entered. This is a simple and practical use case of regular expressions for input sanitization.

---

### 1. Name Validation

```python
pattern = re.compile(r'^[A-Za-z ]+$')
```

**Explanation**:
- The caret `^` and dollar sign `$` are anchors that ensure the entire string must match the pattern from start to end.
- `[A-Za-z ]+` allows uppercase letters, lowercase letters, and spaces only. The `+` ensures at least one character is present.
- This ensures that names like "John Doe" are accepted, while inputs containing numbers or special characters are rejected.

**Accepted Examples**:
- John Doe
- Alice Smith

**Rejected Examples**:
- John123
- @James
- Alice!

---

### 2. Date of Birth Validation

```python
pattern = re.compile(r'\d{2}-\d{2}-\d{4}')
```

**Explanation**:
- `\d{2}` matches exactly two digits (for day and month).
- `\d{4}` matches exactly four digits (for year).
- Hyphens `-` are used as separators between day, month, and year.
- This validates that the input follows the format `DD-MM-YYYY`.

**Note**: This regex only validates the format, not whether the date itself is valid (e.g., `31-02-2000` would still match even though February has no 31st day).

**Accepted Example**:  
- 25-12-1995  
- 01-01-2000

**Rejected Example**:
- 1-1-2000  
- 25/12/1995  
- 1995-12-25

---

### 3. Email ID Validation

```python
pattern = re.compile(r'[a-z0-9]+@gmail.com\Z')
```

**Explanation**:
- `[a-z0-9]+` matches one or more lowercase letters or digits.
- `@gmail.com` ensures that only Gmail addresses are accepted.
- `\Z` ensures the string ends after `.com`, so no extra characters are allowed afterward.
- The email must be entirely in lowercase letters and must belong to Gmail.

**Accepted Examples**:
- john123@gmail.com
- user01@gmail.com

**Rejected Examples**:
- John@Gmail.com (uppercase)
- user@yahoo.com (non-Gmail)
- user@gmail.co (invalid domain)

---

### 4. Mobile Number Validation

```python
pattern = re.compile(r'\d{3}-\d{3}-\d{4}')
```

**Explanation**:
- This matches mobile numbers in the format `XXX-XXX-XXXX`, commonly used in the U.S.
- Each `\d{n}` section enforces the exact number of digits, and hyphens are required between sections.

**Accepted Example**:
- 123-456-7890

**Rejected Examples**:
- 1234567890 (no hyphens)
- 12-3456-7890 (wrong grouping)
- 123-45-67890 (wrong grouping)

---

### 5. Input Handling Logic

- Each field is handled inside a `while` loop.
- The program uses `pattern.fullmatch()` to strictly validate input.
- If the input doesn't match, the user is informed and prompted again.
- Once all inputs are valid, they are printed neatly.

This kind of loop-based validation is common in interactive console applications, ensuring no invalid data is accepted.

---

### Summary

This script demonstrates:
- How to use regular expressions for format validation.
- Looping techniques for repeated input checking.
- Basic structure for safe and clean user input collection in command-line Python programs.

This approach is especially useful when you want to enforce strict input formats without using external libraries.
