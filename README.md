       //simple Login and Registration System using a map to store user information
#include <iostream>
#include <string>
#include <map>

// User class to hold user information
class User {
public:
    std::string username;
    std::string password;
};

// Login and Registration System class
class LoginSystem {
private:
    std::map<std::string, User> users; // Map to store registered users

public:
    void registerUser() {
        std::string username, password;
        std::cout << "Enter username: ";
        std::cin >> username;

        // Check if the username already exists
        if (users.find(username) != users.end()) {
            std::cout << "Username already exists!" << std::endl;
            return;
        }

        std::cout << "Enter password: ";
        std::cin >> password;

        // Create a new user
        User newUser;
        newUser.username = username;
        newUser.password = password;

        // Add the user to the map
        users[username] = newUser;

        std::cout << "Registration successful!" << std::endl;
    }

    void loginUser() {
        std::string username, password;
        std::cout << "Enter username: ";
        std::cin >> username;

        // Check if the username exists
        if (users.find(username) == users.end()) {
            std::cout << "Username not found!" << std::endl;
            return;
        }

        std::cout << "Enter password: ";
        std::cin >> password;

        // Check if the entered password matches the stored password for the username
        if (users[username].password == password) {
            std::cout << "Login successful!" << std::endl;
        } else {
            std::cout << "Invalid password!" << std::endl;
        }
    }
};

int main() {
    LoginSystem loginSystem;
    int choice;

    do {
        std::cout << "Login and Registration System" << std::endl;
        std::cout << "1. Register" << std::endl;
        std::cout << "2. Login" << std::endl;
        std::cout << "3. Exit" << std::endl;
        std::cout << "Enter your choice: ";
        std::cin >> choice;

        switch (choice) {
            case 1:
                loginSystem.registerUser();
                break;
            case 2:
                loginSystem.loginUser();
                break;
            case 3:
                std::cout << "Exiting..." << std::endl;
                break;
            default:
                std::cout << "Invalid choice!" << std::endl;
                break;
        }

        std::cout << std::endl;
    } while (choice != 3);

    return 0;
}

