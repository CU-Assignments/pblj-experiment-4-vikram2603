[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/vOYIK_Kq)
Question 1 - Write a Java Program to implement an Arraylist that stores employee deatils(ID,name,Salary). Allow uswers to (add), (update),(remove,) and (Search) employee.
import java.util.ArrayList;
import java.util.Scanner;

class Employee {
    int id;
    String name;
    double salary;

    Employee(int id, String name, double salary) {
        this.id = id;
        this.name = name;
        this.salary = salary;
    }

    @Override
    public String toString() {
        return "ID: " + id + ", Name: " + name + ", Salary: " + salary;
    }
}

public class EmployeeManagement {
    private ArrayList<Employee> employees = new ArrayList<>();

    public void addEmployee(Employee employee) {
        employees.add(employee);
    }

    public void updateEmployee(int id, String newName, double newSalary) {
        for (Employee emp : employees) {
            if (emp.id == id) {
                emp.name = newName;
                emp.salary = newSalary;
                return;
            }
        }
        System.out.println("Employee not found!");
    }

    public void removeEmployee(int id) {
        employees.removeIf(emp -> emp.id == id);
    }

    public void searchEmployee(int id) {
        for (Employee emp : employees) {
            if (emp.id == id) {
                System.out.println(emp);
                return;
            }
        }
        System.out.println("Employee not found!");
    }

    public static void main(String[] args) {
        EmployeeManagement em = new EmployeeManagement();
        Scanner sc = new Scanner(System.in);

        while (true) {
            System.out.println("\nEmployee Management System");
            System.out.println("1. Add Employee");
            System.out.println("2. Update Employee");
            System.out.println("3. Remove Employee");
            System.out.println("4. Search Employee");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter ID: ");
                    int id = sc.nextInt();
                    sc.nextLine(); // Consume newline
                    System.out.print("Enter Name: ");
                    String name = sc.nextLine();
                    System.out.print("Enter Salary: ");
                    double salary = sc.nextDouble();
                    em.addEmployee(new Employee(id, name, salary));
                    break;
                case 2:
                    System.out.print("Enter Employee ID to update: ");
                    id = sc.nextInt();
                    sc.nextLine(); // Consume newline
                    System.out.print("Enter New Name: ");
                    name = sc.nextLine();
                    System.out.print("Enter New Salary: ");
                    salary = sc.nextDouble();
                    em.updateEmployee(id, name, salary);
                    break;
                case 3:
                    System.out.print("Enter Employee ID to remove: ");
                    id = sc.nextInt();
                    em.removeEmployee(id);
                    break;
                case 4:
                    System.out.print("Enter Employee ID to search: ");
                    id = sc.nextInt();
                    em.searchEmployee(id);
                    break;
                case 5:
                    System.out.println("Exiting...");
                    sc.close();
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice! Please try again.");
            }
        }
    }
}


Question 2 Create a program to collect and stored all tje cards to assist the users in findjng all the cards in a given symbol using collection Interface.
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Card {
    String symbol;
    String value;

    Card(String symbol, String value) {
        this.symbol = symbol;
        this.value = value;
    }

    @Override
    public String toString() {
        return value + " of " + symbol;
    }
}

public class CardCollection {
    private List<Card> cards = new ArrayList<>();

    public void addCard(Card card) {
        cards.add(card);
    }

    public List<Card> findCardsBySymbol(String symbol) {
        List<Card> result = new ArrayList<>();
        for (Card card : cards) {
            if (card.symbol.equalsIgnoreCase(symbol)) {
                result.add(card);
            }
        }
        return result;
    }

    public static void main(String[] args) {
        CardCollection cc = new CardCollection();
        Scanner sc = new Scanner(System.in);

        while (true) {
            System.out.println("\nCard Collection System");
            System.out.println("1. Add Card");
            System.out.println("2. Find Cards by Symbol");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");
            int choice = sc.nextInt();
            sc.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter Card Symbol (e.g., Hearts, Diamonds): ");
                    String symbol = sc.nextLine();
                    System.out.print("Enter Card Value (e.g., Ace, 2, 3): ");
                    String value = sc.nextLine();
                    cc.addCard(new Card(symbol, value));
                    break;
                case 2:
                    System.out.print("Enter Symbol to Search (e.g., Hearts, Diamonds): ");
                    symbol = sc.nextLine();
                    List<Card> foundCards = cc.findCardsBySymbol(symbol);
                    if (foundCards.isEmpty()) {
                        System.out.println("No cards found with symbol: " + symbol);
                    } else {
                        System.out.println("Found Cards:");
                        for (Card card : foundCards) {
                            System.out.println(card);
                        }
                    }
                    break;
                case 3:
                    System.out.println("Exiting...");
                    sc.close();
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice! Please try again.");
            }
        }
    }
}
