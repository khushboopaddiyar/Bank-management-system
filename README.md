# Bank-management-system
import java.util.Scanner;
public class bank
{
	public static void main(String[] args) {
		Scanner sc=new Scanner(System.in);
		System.out.print("How Many Customer U Want to Input : ");
		int n=sc.nextInt();
		ebank  C[]=new ebank[n];
		for(int i=0;i<C.length;i++)
		{   
			C[i]=new ebank();
			
			C[i].openAccount();
		}
		
		
		int ch;
		do
		{
			System.out.println("Main Menu\n 1.Display All \n 2.Search \n 3.Withdrawal \n 4.deposit \n 5.cheque \n 6. Exit");
			
			System.out.println("Ur Choice :");
			ch=sc.nextInt();
			switch(ch)
			{ 
				case 1:
					for(int i=0;i<C.length;i++)
					{
						C[i].showAccount();
					}
					break;
				case 2:
					System.out.print("Enter Account No U Want to Search...: ");
					String acn=sc.next();
					boolean found=false;
					for(int i=0;i<C.length;i++)
					{  
						found=C[i].search(acn);
						if(found)
						{
							break;
						}
					}
					if(!found)
					{
						System.out.println("Search Failed..Account Not Exist..");
					}
					break;

				case 4:
					System.out.print("Enter Account No : ");
			           acn=sc.next();
                 	  found=false;
					for(int i=0;i<C.length;i++)
					{  
						found=C[i].search(acn);
						if(found)
						{
							C[i].deposit();
							break;
						}
					}
					if(!found)
					{
						System.out.println("Search Failed..Account Not Exist..");
					}
					break;
				

				case 3:
					System.out.print("Enter Account No : ");
					acn=sc.next();
					found=false;
					for(int i=0;i<C.length;i++)
					{  
						found=C[i].search(acn);
						if(found)
						{
							C[i].withdrawal();
							break;
						}
					}
					if(!found)
					{
						System.out.println("Search Failed..Account Not Exist..");
					}
					
					break;

				case 5:
					System.out.print("Enter Account No : ");
				acn=sc.next();
				found=false;
				for(int i=0;i<C.length;i++)
				{  
					found=C[i].search(acn);
					if(found)
					{
						C[i].cheque();
						break;
					}
				}
				if(!found)
				{
					System.out.println("Search Failed..Account Not Exist..");
				}
					
					break;

				case 6:
					System.out.println("Good Bye..");
					break;
					
			}
		}
		while(ch!=5);
	}
}
class ebank
{
	String accno;
	String name;
	int  balance;
	String acctype;
	Scanner sc=new Scanner(System.in);
	void openAccount()
	{ 
		System.out.print("Enter Account No: ");
		accno=sc.next();
		System.out.print("Enter Name: ");
		name=sc.next();
		System.out.print("Enter Balance: ");
		balance=sc.nextInt();
		System.out.print("Enter acctype: ");
		acctype=sc.next();
	}

	void showAccount()
	{ 
		System.out.println(accno+","+name+","+balance + ","+acctype);
	}
	void deposit()
	{
		int amt;
		System.out.println("Enter Amount U Want to Deposit : ");
		amt=sc.nextInt();
		balance=balance+amt;
	}

	
	void withdrawal()
	{
		int amt;
		System.out.println("Enter Amount U Want to withdraw : ");
		amt=sc.nextInt();
		if(balance>=amt)
		{ 
			balance=balance-amt;
		}
		else
		{
			System.out.println("Less Balance..Transaction Failed..");
		}
	}
	boolean search(String acn)
	{ 
		if(accno.equals(acn))
		{ 
			showAccount();
			return(true);
		}
		return(false);
	}
	
	void cheque()
	{
		int amt;
		System.out.println("Enter Amount U Want to withdraw for cheque : ");
		amt=sc.nextInt();
		if(balance>=amt)
		{ 
			balance=balance-amt;
		}
		else
		{
			System.out.println("Less Balance..Transaction Failed..");
		}
	}
}
