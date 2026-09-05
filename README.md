def employee_manager():
    directory = {}
    
    while True:
        print("\n==============================")
        print("EMPLOYEE DIRECTORY")
        print("==============================")
        print("1. Add or Update Employee")
        print("2. Remove Employee")
        print("3. Display All Employees")
        print("4. Search Employee")
        print("5. Exit")
        print("------------------------------")
        
        choice = input("Enter your choice (1-5): ").strip()
        
        if choice == '1':
            emp_id = input("Enter Employee ID (e.g., E101): ").strip().upper()
            name = input("Enter Name: ").strip().title()
            department = input("Enter Department: ").strip().title()
            salary = float(input("Enter Salary: $"))
            
            directory[emp_id] = {
                "name": name,
                "department": department,
                "salary": salary
            }
            print(f"Employee {emp_id} has been saved.")
                
        elif choice == '2':
            emp_id = input("Enter Employee ID to remove: ").strip().upper()
            
            if emp_id in directory:
                del directory[emp_id]
                print(f"Employee {emp_id} has been removed.")
            else:
                print(f"Employee ID '{emp_id}' not found.")
                
        elif choice == '3':
            print("\n--- Current Employees ---")
            if not directory:
                print("The directory is empty.")
            else:
                print(f"{'ID':<10} {'NAME':<20} {'DEPARTMENT':<15} {'SALARY':<10}")
                print("-" * 60)
                for emp_id, info in directory.items():
                    print(f"{emp_id:<10} {info['name']:<20} {info['department']:<15} ${info['salary']:.2f}")
            print("-------------------------")
            
        elif choice == '4':
            emp_id = input("Enter Employee ID to search: ").strip().upper()
            
            if emp_id in directory:
                info = directory[emp_id]
                print(f"Found: {info['name']} | Dept: {info['department']} | Salary: ${info['salary']:.2f}")
            else:
                print(f"Employee ID '{emp_id}' not found.")
                
        elif choice == '5':
            print("Exiting Employee Directory. Goodbye!")
            break
            
        else:
            print("Invalid choice. Please enter a number between 1 and 5.")

if __name__ == "__main__":
    employee_manager()
