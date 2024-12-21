# ATM_Machine
It is core java mini-project using a Exception. where user see the  how many funds in his/her account . and debit. if  wrong pin and  exceed the fund that it user get an  Exception


package study.dms;
import java.util.*;



class bank
{
	private int pin;
	private double bal;
	
	bank(int pin , double bal){
		this.pin = pin;
		this.bal = bal;
		
	}
	public void setBal(double bal) {
		this.bal = bal;
	}
	public double getBal(double newbal) {
		return this.bal= newbal;
	}
	public void setPin(int pin) {
		this.pin = pin;
	}
	public int getPin(int newpin) {
		return this.pin= newpin;
	}
}
public class ATM_Machine {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
		
		
		System.out.println("**********WELCOME TO SBI BANK********* ");
		
		System.out.println("**********ENTER YOUR DEBIT CARD**********");
		System.out.println("  1.  ACCOUNT INFORMATION   ");
		System.out.println("  2.  CASH WITHDRAWAL       ");
		System.out.println("  3.  EXIT             ");
		
		for (;;) 
		{
			System.out.print("SELECT BELOW OPTION :-  ");
			int option= sc.nextInt();
			
			switch (option) {
			case 1: accountInformation(sc);break;
			case 2: debitmoney(sc);break;
			case 3: System.exit(0);break;
			default:
				System.out.println();
				System.out.println("**WRONG OPTION SELECTED**");
				System.out.println();
			}
			
		}
	}
	public static void accountInformation(Scanner sc) {
		
		
		bank obj = new bank(1234, 10000.00);
		System.out.print("enter your pin :-  ");
		int p = sc.nextInt();
		
		if (!(p == obj.getPin(1234))) {
			throw new invalidPinException();
			
		}
		else {
			System.out.println("Your Available Balance :-->   "+obj.getBal(10000.00));
			System.out.println();
			System.out.println("***************THANKS FOR VISITING************");
			System.out.println();
			System.out.println();
		}
		
		
	}
	public static void debitmoney(Scanner sc) 
	{
				bank obj = new bank(1234, 10000.00);
				System.out.print("enter your pin :-  ");
				int p1 = sc.nextInt();
				if (!(p1 == obj.getPin(1234))) {
					throw new invalidPinException();
			
				}
			else {
			System.out.print("entered your withdrow Amount :-");
			
				}	
				
				double amount = sc.nextDouble();
				if (!(amount <= obj.getBal(10000))) {
					throw new invalidBalanceException();
			
				}
				else {
					System.out.println("Get your funds :-"+amount);
				}
				
				

	}
}
class invalidPinException extends RuntimeException {
	invalidPinException(){
		super("Wrong pin entered");
		
	}
}
class invalidBalanceException extends RuntimeException{
	invalidBalanceException()
	{
		super("insufficient funds");
	}
}
