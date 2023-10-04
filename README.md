#include <iostream>
#include <vector>
#include <string>

using namespace std;

// Function to display the to-do list
void displayTasks(const vector<string>& tasks) {
    cout << "To-Do List:" << endl;
    for (int i = 0; i < tasks.size(); ++i) {
        cout << i + 1 << ". " << tasks[i] << endl;
    }
}

int main() {
    vector<string> tasks;
    int choice;

    while (true) {
        cout << "To-Do List Manager" << endl;
        cout << "1. Add Task" << endl;
        cout << "2. View Tasks" << endl;
        cout << "3. Delete Task" << endl;
        cout << "4. Quit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1: {
                string task;
                cout << "Enter a task: ";
                cin.ignore(); // Consume the newline character
                getline(cin, task);
                tasks.push_back(task);
                cout << "Task added!" << endl;
                break;
            }
            case 2: {
                if (tasks.empty()) {
                    cout << "The to-do list is empty." << endl;
                } else {
                    displayTasks(tasks);
                }
                break;
            }
            case 3: {
                if (tasks.empty()) {
                    cout << "The to-do list is empty." << endl;
                } else {
                    int taskIndex;
                    cout << "Enter the task number to delete: ";
                    cin >> taskIndex;
                    if (taskIndex >= 1 && taskIndex <= tasks.size()) {
                        tasks.erase(tasks.begin() + taskIndex - 1);
                        cout << "Task deleted!" << endl;
                    } else {
                        cout << "Invalid task number." << endl;
                    }
                }
                break;
            }
            case 4: {
                cout << "Exiting the program." << endl;
                return 0;
            }
            default:
                cout << "Invalid choice. Please enter a valid option." << endl;
        }
    }

    return 0;
}
