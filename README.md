import time

def authenticate_user():
    stored_password = "12345"  # Predefined password
    attempts = 0
    max_attempts = 5
    
    while attempts < max_attempts:
        password = input("Enter your 5-digit banking password: ")
        
        if not password.isdigit() or len(password) != 5:
            print("Invalid input! Password must be exactly 5 digits.")
            continue
        
        if password == stored_password:
            print("Access granted. Welcome to your bank account!")
            return True
        else:
            attempts += 1
            print(f"Incorrect password. Attempts remaining: {max_attempts - attempts}")
    
    print("Too many incorrect attempts. Please reset your password at the bank.")
    return False

def banking_services():
    balance = 1000  # Initial balance
    transactions =[]
    
    while True:
        print("\nBanking Services:")
        print("1. View Available Balance")
        print("2. Deposit Money")
        print("3. Withdraw Money")
        print("4. View Statement")
        print("5. Exit")
        
        choice = input("Enter your choice: ")
        
        if choice == "1":
            print(f"Your available balance is: ${balance}")
        elif choice == "2":
            amount = float(input("Enter deposit amount: "))
            if amount > 0:
                balance += amount
                transactions.append(f"Deposited: ${amount}")
                print("Deposit successful!")
                print(f"Updated balance: ${balance}")
            else:
                print("Invalid amount!")
        elif choice == "3":
            amount = float(input("Enter withdrawal amount: "))
            if 0 < amount <= balance:
                balance -= amount
                transactions.append(f"Withdrawn: ${amount}")
                print("Withdrawal successful!")
                print(f"Updated balance: ${balance}")
            else:
                print("Invalid amount or insufficient funds!")
        elif choice == "4":
            print("\nTransaction Statement:")
            for transaction in transactions:
                print(transaction)
            print(f"Current balance: ${balance}")
        elif choice == "5":
            print("Exiting banking services.")
            break
        else:
            print("Invalid choice. Please select a valid option.")

def main():
    print("Welcome to Secure Bank!")
    time.sleep(1)
    if authenticate_user():
        banking_services()
    else:
        print("Exiting system for security reasons.")

if __name__ == "__main__":
    main()
