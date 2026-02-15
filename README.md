tasks = []

while True:
    print("\nCommands: add, view, complete, exit")
    command = input("Enter command: ").strip().lower()

    if command == "add":
        task = input("Enter task description: ").strip()
        if task:
            tasks.append(task)
            print(f'Task "{task}" added.')
        else:
            print("Task cannot be empty.")

    elif command == "view":
        if not tasks:
            print("No tasks available.")
        else:
            print("\nYour Tasks:")
            for i, task in enumerate(tasks, start=1):
                print(f"{i}. {task}")

    elif command == "complete":
        if not tasks:
            print("No tasks to complete.")
            continue

        try:
            index = int(input("Enter task number to complete: "))
            if 1 <= index <= len(tasks):
                completed_task = tasks[index - 1]

                # Option 1: Mark task as completed
                tasks[index - 1] = "[x] " + completed_task
                print(f'Task marked as completed: {completed_task}')

                # Option 2 (alternative): Remove task
                # del tasks[index - 1]

            else:
                print("Invalid task number.")
        except ValueError:
            print("Please enter a valid number.")

    elif command == "exit":
        print("Goodbye! 👋")
        break

    else:
        print("Invalid command. Please try again.")
