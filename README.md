
# Student Record Management System
# Language: Python 3

# Dictionary to store student records
# Key = Roll Number
# Value = Tuple (Name, Course, Marks)

students = {}


# 1. ADD STUDENT
def add_student():
    print("\n--- Add Student ---")

    try:
        roll = int(input("Enter Roll Number: "))

        if roll in students:
            print(f"Roll number {roll} already exists.")
            return

        name = input("Enter Student Name: ")
        course = input("Enter Course: ")
        marks = float(input("Enter Marks (0-100): "))

        if marks < 0 or marks > 100:
            print("Marks must be between 0 and 100.")
            return

        # Store student details as a tuple
        students[roll] = (name, course, marks)

        print(f"Record added: {roll} | {name} | {course} | {marks:g}")

    except ValueError:
        print("Invalid input! Please enter valid values.")


# 2. VIEW ALL STUDENTS
def view_students():
    print("\n--- Student Records ---")

    if not students:
        print("No student records found.")
        return

    # List of table headings
    headers = ["Roll No.", "Name", "Course", "Marks"]

    print("-" * 65)
    print(f"{headers[0]:<12}{headers[1]:<18}{headers[2]:<18}{headers[3]:<10}")
    print("-" * 65)

    for roll, details in sorted(students.items()):
        name, course, marks = details

        print(f"{roll:<12}{name:<18}{course:<18}{marks:<10g}")

    print("-" * 65)


# 3. SEARCH STUDENT
def search_student():
    print("\n--- Search Student ---")

    try:
        roll = int(input("Enter Roll Number to Search: "))

        if roll in students:
            name, course, marks = students[roll]

            print("\nStudent Found!")
            print("Roll Number:", roll)
            print("Name:", name)
            print("Course:", course)
            print("Marks:", marks)

        else:
            print(f"Roll number {roll} not found.")

    except ValueError:
        print("Please enter a valid roll number.")


# 4. UPDATE STUDENT
def update_student():
    print("\n--- Update Student ---")

    try:
        roll = int(input("Enter Roll Number to Update: "))

        if roll not in students:
            print(f"Roll number {roll} not found.")
            return

        name, course, old_marks = students[roll]

        print("Current Marks:", old_marks)

        new_marks = float(input("Enter New Marks: "))

        if new_marks < 0 or new_marks > 100:
            print("Marks must be between 0 and 100.")
            return

        # Update the existing tuple
        students[roll] = (name, course, new_marks)

        print("Student record updated successfully!")
        print(f"Updated: {roll} | {name} | {course} | {new_marks:g}")

    except ValueError:
        print("Please enter valid input.")


# 5. DELETE STUDENT
def delete_student():
    print("\n--- Delete Student ---")

    try:
        roll = int(input("Enter Roll Number to Delete: "))

        if roll in students:
            del students[roll]
            print(f"Record of Roll Number {roll} deleted successfully.")

        else:
            print(f"Roll number {roll} not found.")

    except ValueError:
        print("Please enter a valid roll number.")


# MAIN MENU
def main():
    while True:

        print("\n===================================")
        print("   STUDENT RECORD MANAGEMENT SYSTEM")
        print("===================================")

        print("1. Add Student")
        print("2. View All Students")
        print("3. Search Student")
        print("4. Update Student Marks")
        print("5. Delete Student")
        print("6. Exit")

        print("===================================")

        try:
            choice = int(input("Enter Your Choice (1-6): "))

            if choice == 1:
                add_student()

            elif choice == 2:
                view_students()

            elif choice == 3:
                search_student()

            elif choice == 4:
                update_student()

            elif choice == 5:
                delete_student()

            elif choice == 6:
                print("Thank you for using Student Record Management System!")
                break

            else:
                print("Invalid choice! Please select between 1 and 6.")

        except ValueError:
            print("Please enter a valid menu option.")


# Program Execution
if __name__ == "__main__":
    main()
