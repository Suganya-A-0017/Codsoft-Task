# Codsoft-Task
import json

# In-memory contact list
contacts = []

def add_contact():
    name = input("Enter Name: ")
    phone = input("Enter Phone Number: ")
    email = input("Enter Email: ")
    address = input("Enter Address: ")
    contacts.append({"name": name, "phone": phone, "email": email, "address": address})
    print("Contact added successfully!")

def view_contacts():
    if not contacts:
        print("No contacts found.")
        return
    for i, contact in enumerate(contacts, start=1):
        print(f"{i}. {contact['name']} - {contact['phone']}")

def search_contact():
    search = input("Search by Name or Phone: ")
    results = [c for c in contacts if search.lower() in c["name"].lower() or search in c["phone"]]
    if results:
        for contact in results:
            print(contact)
    else:
        print("No contacts found.")

def update_contact():
    search = input("Enter Name or Phone of Contact to Update: ")
    for contact in contacts:
        if search.lower() in contact["name"].lower() or search in contact["phone"]:
            print("Current Details:", contact)
            contact["name"] = input("New Name: ") or contact["name"]
            contact["phone"] = input("New Phone: ") or contact["phone"]
            contact["email"] = input("New Email: ") or contact["email"]
            contact["address"] = input("New Address: ") or contact["address"]
            print("Contact updated!")
            return
    print("Contact not found.")

def delete_contact():
    search = input("Enter Name or Phone of Contact to Delete: ")
    for contact in contacts:
        if search.lower() in contact["name"].lower() or search in contact["phone"]:
            contacts.remove(contact)
            print("Contact deleted!")
            return
    print("Contact not found.")

def main_menu():
    while True:
        print("\nContact Management System")
        print("1. Add Contact")
        print("2. View Contacts")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")
        choice = input("Enter your choice: ")
        
        if choice == "1":
            add_contact()
        elif choice == "2":
            view_contacts()
        elif choice == "3":
            search_contact()
        elif choice == "4":
            update_contact()
        elif choice == "5":
            delete_contact()
        elif choice == "6":
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main_menu()