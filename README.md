def calculate_sgpa(credit_hours, grades):
    total_credit_points = 0
    total_credit_hours = 0

    for credit, grade in zip(credit_hours, grades):
        if grade == 'O':
            grade_point = 10.0
        elif grade == 'A+':
            grade_point = 9.0
        elif grade == 'A':
            grade_point = 8.0
        elif grade == 'B+':
            grade_point = 7.0
        elif grade == 'B':
            grade_point = 6.0
        elif grade == 'C':
            grade_point =5.0

        total_credit_points += credit * grade_point
        total_credit_hours += credit

    sgpa = total_credit_points / total_credit_hours
    return sgpa

def calculate_cgpa(previous_cgpa, previous_credit_hours, sgpa, current_credit_hours):
    total_credit_points = previous_cgpa * previous_credit_hours + sgpa * current_credit_hours
    total_credit_hours = previous_credit_hours + current_credit_hours

    cgpa = total_credit_points / total_credit_hours
    return cgpa

def main():
    # Input for current semester
    subjects = int(input("Enter the number of subjects in the current semester: "))
    credit_hours = []
    grades = []

    for i in range(subjects):
        credit = float(input(f"Enter credit hours for subject {i + 1}: "))
        grade = input(f"Enter grade for subject {i + 1} (A, B, C, D, etc.): ").upper()

        credit_hours.append(credit)
        grades.append(grade)

    # Input for previous CGPA
    previous_cgpa = float(input("Enter your previous CGPA: "))
    previous_credit_hours = float(input("Enter your previous total credit hours: "))

    # Calculate SGPA for the current semester
    sgpa = calculate_sgpa(credit_hours, grades)
    print(f"\nYour SGPA for the current semester is: {sgpa:.2f}")

    # Calculate CGPA
    cgpa = calculate_cgpa(previous_cgpa, previous_credit_hours, sgpa, sum(credit_hours))
    print(f"Your updated CGPA is: {cgpa:.2f}")

if __name__ == "__main__":
    main()
