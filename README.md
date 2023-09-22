# To-Do-List
A To-Do List application is a useful project that helps users manage and organize their tasks efficiently. This project aims to create a command-line or GUI-based application using Python, allowing  users to create, update, and track their to-do lists
import os

# Function to display the To-Do list
def display_todo_list():
    with open("todo.txt", "r") as file:
        tasks = file.readlines()
        if not tasks:
            print("Your To-Do list is empty.")
        else:
            print("Your To-Do List:")
            for i, task in enumerate(tasks, start=1):
                print(f"{i}. {task.strip()}")

# Function to add a task to the To-Do list
def add_task():
    task = input("Enter the task to add: ")
    with open("todo.txt", "a") as file:
        file.write(task + "\n")
    print(f"Task '{task}' added to your To-Do list.")

# Function to mark a task as done
def mark_done():
    display_todo_list()
    task_number = int(input("Enter the task number to mark as done: ")) - 1
    with open("todo.txt", "r") as file:
        tasks = file.readlines()
    if 0 <= task_number < len(tasks):
        done_task = tasks.pop(task_number)
        with open("todo.txt", "w") as file:
            file.writelines(tasks)
        print(f"Task '{done_task.strip()}' marked as done.")
    else:
        print("Invalid task number.")

# Main program loop
while True:
    print("\nOptions:")
    print("1. Display To-Do List")
    print("2. Add a Task")
    print("3. Mark a Task as Done")
    print("4. Quit")

    choice = input("Enter your choice (1/2/3/4): ")

    if choice == "1":
        display_todo_list()
    elif choice == "2":
        add_task()
    elif choice == "3":
        mark_done()
    elif choice == "4":
        print("Goodbye!")
        break
    else:
        print("Invalid choice. Please try again.")
