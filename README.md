# java-project
Develop a scenario based program by using Method Overloading for processing the payment using different available options like Cash Payment, Credit Card and Debit Card Payment

package com.raj.blc;
public class Payment
{
	public void  makePayment(double amount) 
	{
		boolean validateAmount = validateAmount(amount);
		if(validateAmount)
		{
			System.out.println("Processing  payment via cash");
			System.out.println("Amount paid via Rs"+amount);
			System.out.println("Payment successfully");
		}
	}
	private boolean validateAmount(double Amount)
	{
		if(Amount<=0) 
		{
			System.err.println("Amount cannot be negative");
			return false;
		}
		else 
		{
			return true;
		}
		
		}
	
	public void makepayment(String cardHolderName, String creditCardNumber,double amount) 
	{
		boolean val=validateCardNumber(creditCardNumber);
		
		if(val)
		{
		
			  System.out.println("Processing payment via Credit Card");
			  System.out.println("Card holder name"+cardHolderName);
			  System.out.println("Card Number :  **** **** **** "+maskCardNumber(creditCardNumber));
			  System.out.println("Amount="+amount);
			  System.out.println("Payment successfully");
		}
		else
		{
			System.out.println("Invalid card no");
		}
		
	}
	
	private boolean validateCardNumber(String cardNumber) 
	{
		if(cardNumber.length()==16)
		{
			return true;
		}
		else 
		{
			return false;
		}	
}
	
	
	public void makepayment(String debitCardNumber, double amount)
	{
		
		
		
		if(validateCardNumber(debitCardNumber)) {
			System.out.println("Processing payment via Debit Card...");
		
			  System.out.println("Card Number :  **** **** **** "+maskCardNumber(debitCardNumber));
			  System.out.println("Amount="+amount);
			  System.out.println("Payment successfully");
			
			
		}
		else
		{
			System.out.println("Invalid card no");
		}	
	}


	private String maskCardNumber(String cardNumber) 
	{
		
		return ""+cardNumber.substring(12, cardNumber.length());
	}
}

//elc package
package com.raj.elc;

import java.util.Scanner;

import com.raj.blc.Payment;
public class PaymentProcess {

	public static void main(String[] args) {
		Scanner sc=new Scanner(System.in);
		System.out.println("Payment Menu");
		System.out.println("Please select any one Payment Method from the Menu :");
System.out.println("\t\t 1) Payment by using Cash "
		+ "\\t\\t 2) Payment by using Credit Card "
		+ "\\t\\t 3) Payment by using Debit Card");

		System.out.println("Enter the Option :- ");
		int option=sc.nextInt();
		Payment p=new Payment();
		
switch(option) 
{
case 1: System.out.println("Enter the amount  you want to pay through cash:");
               double amount=sc.nextDouble();
               p.makePayment(amount);
               break;
     
case 2:
	  System.out.println("Enter  your name");
	  String cname=sc.nextLine();
	  cname=sc.nextLine();
	  System.out.println("Enter your 16 digit Credit Card Number :");
	  String cre=sc.next();
	  System.out.println("Enter your amount");
	  double amt=sc.nextDouble();
	     p.makepayment(cname, cre, amt);
	     break;
case 3:
	System.out.println("Enter your 16 digit Debit Card Number");
	String debitCardNumber=sc.nextLine();
	debitCardNumber=sc.nextLine();
	System.out.println("Enter amout ");
	double amt1=sc.nextDouble();
	p.makepayment(debitCardNumber, amt1);
	break;	
	
}

}
}

	

	
	

