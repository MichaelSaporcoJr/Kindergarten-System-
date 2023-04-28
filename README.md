# Kindergarten-System-
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package com.mycompany.kindergarten;

import java.util.ArrayList;
import java.util.Scanner;

public class Kindergarten {
    
    public static class Student {
        public String firstName;
        public String middleName;
        public String lastName;
        public int age;
        public String gender;
        public String address;
        public String contactNumber;
        public String classSchedule;
        public String parentName;
        public int parentContact;
        
        public Student(String firstName, String middleName, String lastName, int age, String gender, String address, String contactNumber, String classSchedule, String parentName, int parentContact) {
            this.firstName = firstName;
            this.middleName = middleName;
            this.lastName = lastName;
            this.age = age;
            this.gender = gender;
            this.address = address;
            this.contactNumber = contactNumber;
            this.classSchedule = classSchedule;
            this.parentName = parentName;
            this.parentContact = parentContact;
        }
    }
    

public static void main(String[] args) {
    
    
        
        Scanner scanner = new Scanner (System.in);
        String firstName, middleName, lastName, address, contactNumber, classSchedule = null, gender, parentName;
        int age;
        int parentContact;
        int morningStudents = 0; // count of students enrolled in morning shift
        int afternoonStudents = 0; // count of students enrolled in afternoon shift
        ArrayList<Student> enrolledStudents = new ArrayList<>(); // list of enrolled students
        
        System.out.println("Welcome to the Kindergarten Enrollment System");
        
        boolean addMoreStudents; 
        do {
            System.out.println("\nPlease enter the following information:");
            
            // Collect basic information
            System.out.print("First Name: ");
            firstName = scanner.nextLine();
            
            System.out.print("Middle Name: ");
            middleName = scanner.nextLine();
            
            System.out.print("Last Name: ");
            lastName = scanner.nextLine();
            
            System.out.print("Age: ");
            age = scanner.nextInt();
            scanner.nextLine(); // consume newline
            
            System.out.print("Gender: ");
            gender = scanner.nextLine();
            
            System.out.print("Address: ");
            address = scanner.nextLine();
            
            System.out.print("Contact Number: ");
            contactNumber = scanner.nextLine();
            
            // Select class schedule
            int choice;
            boolean invalidChoice;
            do {
                invalidChoice = false;
                System.out.println("\nPlease select a class schedule:");
                System.out.println("1. Morning");
                System.out.println("2. Afternoon");

                System.out.print("Enter choice: ");
                choice = scanner.nextInt();
                scanner.nextLine(); // consume newline

                switch (choice) {
                    case 1:
                        if (morningStudents > 12) {
                            System.out.println("Sorry, the morning shift is already full.");
                            invalidChoice = true;
                        } else {
                            classSchedule = "9:00am - 11:00am";
                            morningStudents++;
                        }
                        break;
                    case 2:
                        if (afternoonStudents > 12) {
                            System.out.println("Sorry, the afternoon shift is already full.");
                            invalidChoice = true;
                        } else {
                            classSchedule = "1:00pm - 3:00pm";
                            afternoonStudents++;
                        }
                        break;
                    default:
                        System.out.println("Invalid choice. Please try again.");
                        invalidChoice = true;
                        break;
                }
            }while (invalidChoice);
            
            // Collect parent information
            System.out.println("\nPlease enter the following information about the parent/guardian:");
            
            System.out.print("Name: ");
            parentName = scanner.nextLine();
            
            System.out.print("Contact Number: ");
            parentContact = scanner.nextInt();
            
            // Display enrollment details
            System.out.println("\nEnrollment Details:");
            System.out.println("-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------");
            System.out.printf("|%-20s|%-20s|%-20s|%-20s|%-10s|%-15s|%-20s|%-20s|\n", "Name", "Age", "Gender", "Contact Number", "Class Schedule", "Address", "Parent's Name", "Parent's Contact Number");
            System.out.println("-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------");
            System.out.printf("|%-20s|%-20d|%-20s|%-20s|%-10s|%-15s|%-20s|%-20s|\n", firstName + " " + middleName + " " + lastName, age, gender, contactNumber, classSchedule, address, parentName, parentContact);
            
            // Add student to the list of enrolled students and schedules
             enrolledStudents.add(new Student(firstName, middleName, lastName, age, gender, address, contactNumber, classSchedule, parentName, parentContact));
            
            // Check if user wants to add more students
            
            Scanner scanner1 = new Scanner (System.in);
            System.out.print("\nDo you want to add another student? (Y/N): ");
            String choice2 = scanner1.nextLine();
            addMoreStudents = choice2.equalsIgnoreCase("Y");
            
            
        } while (addMoreStudents);
        
        // Display schedule of enrolled students
        System.out.println("\nList of Enrolled Students:");
        System.out.println("-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------");
        System.out.printf("|%-20s|%-20s|%-20s|%-10s|%-15s|%-20s|\n", "Name", "Age", "Gender", "Class Schedule", "Address", "Contact Number");
        System.out.println("-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------");
        for (Student student : enrolledStudents) {
        System.out.printf("|%-20s|%-20d|%-20s|%-10s|%-15s|%-20s|\n", student.firstName + " " + student.middleName + " " + student.lastName, student.age, student.gender, student.classSchedule, student.address, student.contactNumber);
    }
    System.out.println("-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------");
}
}


    

