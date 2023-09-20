# A

def read_csv_and_print_table(filename):
    with open(filename, 'r') as file:
        in_quotes = False
        current_column = ""
        for char in file.read():
            if char == '"':
                in_quotes = not in_quotes
            elif char == ',' and not in_quotes:
                print(current_column, end=" | ")
                current_column = ""
            elif char == '\n':
                print(current_column)
                current_column = ""
            else:
                current_column += char

    # Add this final print statement to handle the last column
    if current_column:
        print(current_column)

filename = "/content/Salary_Data.csv"
read_csv_and_print_table(filename)
