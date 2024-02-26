# ATM-Interface
import java.util.Scanner;

    class ATM {
        private BankAccount account;

        public ATM(BankAccount account) {
            this.account = account;
        }

        
        public void withdraw(double amount) {
            if (amount > 0 && amount <= account.getBalance()) {
                account.withdraw(amount);
                System.out.println(+ amount + "rs Withdrawal is successful");
            } else {
                System.out.println("Invalid Amount.");
            }
        }

        
        public void deposit(double amount) {
            if (amount > 0) {
                account.deposit(amount);
                System.out.println(  amount + "rs is Deposited  successfully");
            } else {
                System.out.println("Invalid Amount.");
            }
        }

        public void checkBalance() {
            System.out.println(" Current Balance is rs" + account.getBalance());
        }
    }

    
    class BankAccount { //user bankaccount details
        private double balance;

        public BankAccount(double balance) {
            this.balance = balance;
        }

        public double getBalance() {
            return balance;
        }

        public void withdraw(double amount) {
            balance =balance - amount;
        }

        public void deposit(double amount) {
            balance =balance + amount;
        }
    }

    public class atm_interface_8586 {
        public static void main(String[] args) {
            BankAccount userAccount = new BankAccount(500000); 
            ATM atm = new ATM(userAccount);
            Scanner scanner = new Scanner(System.in);
            int choice;

            do {
                System.out.println("How can I help you ??");
                System.out.println("1. Withdraw");
                System.out.println("2. Deposit");
                System.out.println("3. Check Balance");
                System.out.println("4. Exit");
                System.out.print("Enter your choice: ");
                choice = scanner.nextInt();

                switch (choice) {
                    case 1:
                        System.out.print("Enter amount to withdraw: ");
                        double withdrawAmount = scanner.nextDouble();
                        atm.withdraw(withdrawAmount);
                        break;
                    case 2:
                        System.out.print("Enter amount to deposit: ");
                        double depositAmount = scanner.nextDouble();
                        atm.deposit(depositAmount);
                        break;
                    case 3:
                        atm.checkBalance();
                        break;
                    case 4:
                        System.out.println("Thank you !!");
                        break;
                    default:
                        System.out.println("Invalid choice!!");
                }
            } while (choice != 4);

            scanner.close();
        }
    }


