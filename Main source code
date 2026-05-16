#include <iostream>
#include <string>
using namespace std;
/* ============ INTERFACE ============ */
class IMedical {
public:
    virtual void showMedicalInfo() = 0;};
/* ============ ABSTRACT CLASS ============ */
class Person {
protected:
    int id;
    string name;
    int age;
public:
    Person(int i = 0, string n = "", int a = 0) {
        id = i;
        name = n;
        age = a;}
    virtual void displayInfo() = 0;   // Polymorphism
};
/* ============ PATIENT ============ */
class Patient : public Person, public IMedical {
    string disease;
public:
    Patient(int i = 0, string n = "", int a = 0, string d = "")
        : Person(i, n, a) {
        disease = d;}
    void displayInfo() {
        cout << "Patient ID: " << id << endl;
        cout << "Name: " << name << endl;
        cout << "Age: " << age << endl;}
    void showMedicalInfo() {
        cout << "Disease: " << disease << endl;} };
/* ============ SCHEDULE (COMPOSITION) ============ */
class Schedule {
    string timing;
public:
    Schedule(string t = "Not Set") {
        timing = t;}
    void show() {
        cout << "Timing: " << timing << endl;}};
/* ============ DOCTOR ============ */
class Doctor : public Person {
    string specialization;
    Schedule schedule;   // Composition
public:
    Doctor(int i = 0, string n = "", int a = 0, string s = "", string t = "")
        : Person(i, n, a), schedule(t) {
        specialization = s;}
    void displayInfo() {
        cout << "Doctor ID: " << id << endl;
        cout << "Name: " << name << endl;
        cout << "Age: " << age << endl;
        cout << "Specialization: " << specialization << endl;
        schedule.show();}};
/* ============ APPOINTMENT ============ */
class Appointment {
    Patient patient;
    Doctor doctor;
public:
    Appointment(Patient p = Patient(), Doctor d = Doctor())
        : patient(p), doctor(d) {}
    void show() {
        cout << "\n--- Appointment Details ---\n";
        patient.displayInfo();
        patient.showMedicalInfo();
        doctor.displayInfo();}};
/* ============ HOSPITAL SYSTEM ============ */
class HospitalSystem {
    Patient patients[5];
    Doctor doctors[5];
    Appointment appointments[5];
    int pCount;
    int dCount;
    int aCount;
public:
    HospitalSystem() {
        pCount = dCount = aCount = 0;}
    void addPatient() {
        if (pCount >= 5) {
            cout << "Patient limit reached!\n";
            return;
        }
        int id, age;
        string name, disease;
        cout << "Enter Patient ID: ";
        cin >> id;
        cin.ignore();
        cout << "Enter Name: ";
        getline(cin, name);
        cout << "Enter Age: ";
        cin >> age;
        cin.ignore();
        cout << "Enter Disease: ";
        getline(cin, disease);
        patients[pCount++] = Patient(id, name, age, disease);
        cout << "Patient Added!\n";}
    void addDoctor() {
        if (dCount >= 5) {
            cout << "Doctor limit reached!\n";
            return;}
        int id, age;
        string name, spec, time;
        cout << "Enter Doctor ID: ";
        cin >> id;
        cin.ignore();
        cout << "Enter Name: ";
        getline(cin, name);
        cout << "Enter Age: ";
        cin >> age;
        cin.ignore();
        cout << "Enter Specialization: ";
        getline(cin, spec);
        cout << "Enter Timing: ";
        getline(cin, time);
        doctors[dCount++] = Doctor(id, name, age, spec, time);
        cout << "Doctor Added!\n";}
    void bookAppointment() {
        if (pCount == 0 || dCount == 0) {
            cout << "Add patient and doctor first!\n";
            return;}
        appointments[aCount++] =
            Appointment(patients[0], doctors[0]);
        cout << "Appointment Booked!\n";}
    void showAppointments() {
        for (int i = 0; i < aCount; i++) {
            appointments[i].show();}}};
/* ============ MAIN ============ */
int main() {
    HospitalSystem system;
    int choice;
    do {
        cout << "\n--- Hospital Management System ---\n";
        cout << "1. Add Patient\n";
        cout << "2. Add Doctor\n";
        cout << "3. Book Appointment\n";
        cout << "4. View Appointments\n";
        cout << "0. Exit\n";
        cout << "Enter Choice: ";
        cin >> choice;
        switch (choice) {
            case 1: system.addPatient(); break;
            case 2: system.addDoctor(); break;
            case 3: system.bookAppointment(); break;
            case 4: system.showAppointments(); break;
            case 0: cout << "Exiting...\n"; break;
            default: cout << "Invalid Choice!\n";}
    } while (choice != 0);
    return 0;}
