import java.util.Scanner;

public class ATM {

    public static void main(final String[] args){
        final int correctPIN = 2710;
        double balance = 20000;
        int pin;
        int attempts = 0;

        final Scanner sc = new Scanner(System.in);

        do {
            System.out.print("Enter your PIN: ");
            pin = sc.nextInt();
            attempts++;

            if (pin == correctPIN) {
                System.out.println("PIN Verified!\n");
                int choice;

                do {
                    System.out.println("1. Check Balance");
                    System.out.println("2. Withdraw");
                    System.out.println("3. Deposit");
                    System.out.println("4. Exit");
                    System.out.print("Enter your choice: ");
                    choice = sc.nextInt();

                    if (choice == 1) {
                        System.out.println("Your current balance is rupees: " + balance);

                    } else if (choice == 2) {
                        System.out.print("Enter amount to withdraw: rupees ");
                        final double amount = sc.nextDouble();
                        if (amount <= balance) {
                            balance -= amount;
                            System.out.println("Withdrawal of rupees " + amount + " successful.");
                            System.out.println("Remaining balance: rupees " + balance);
                        } else {
                            System.out.println("Insufficient balance.");
                        }

                    } else if (choice == 3) {
                        System.out.print("Enter amount to deposit: rupees ");
                        final double deposit = sc.nextDouble();
                        balance += deposit;
                        System.out.println("Deposit of rupees " + deposit + " successful.");
                        System.out.println("Updated balance: rupees " + balance);

                    } else if (choice == 4) {
                        System.out.println("Exiting. Thank you for using ATM.");
                        

                    } else {
                        System.out.println("Invalid choice. Please try again.");
                    }

                    System.out.println(); // spacing

                } while (choice != 4);

                break; // Exit after successful session

            } else {
                System.out.println("Incorrect PIN. Attempts left: " + (3 - attempts));
            }

        } while (attempts < 3);

        if (attempts == 3 && pin != correctPIN) {
            System.out.println("Card blocked due to 3 incorrect attempts.");
        }

        sc.close();
    }
}

