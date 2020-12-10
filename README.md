#include<stdio.h>                                        //header file
#include<iostream>

#define r 5
#define c 2
using namespace std;

class bank                                                            //class
{
    char name[100], add[100],k;
    int balance;
    public:                                                           //access specifier
         void open_account(int (&account)[r][c],int count);                                         //function to get data from user
         void deposit_money(int (&account)[r][c]);                                        // function to accept amount and substract from the balance amount
         void withdraw_money(int (&account)[r][c]);                                       //function to accept amount and add to balance
         void display_balance(int (&account)[r][c]);                                      // function to diaplay allaccount deposit list



};                                                                    //class end here

void bank :: open_account(int (&account)[r][c],int count)
                          {

                              cout<<"enter you full name :: ";
                              cin.ignore();                            //to encounter the buffer error
                              cin.getline(name,100);                   //to read a data either file from user through keyboard
                              cout<<"enter your address ::";
                              cin.ignore();
                              cin.getline(add,100);
                              cout<<"what type of account you want to open saving (s) or current (c)";
                              cin>>k;
                              cout<<"enter amount for deposit\n";
                              cin>>account[count][1];
                              cout<<"!!!Your account is created!!!\n";
                              cout<<"->Your account no = "<<account[count][0];
                              cout<<"\n";


                          }

void bank::deposit_money(int (&account)[r][c])
{
    int a,no,i,match=10;

                             cout<<"Enter the account number : ";
                             cin>>no;
                             for(i=0;i<5;i++){
                             	if(account[i][0]==no){
                             		match=i;
								 }
							 }
							 if (match==10){
							 	cout<<"No account found ";

							 }
							 else{

							 cout<<" enter how much you deposit :: ";
                             cin>>a;
                             account[match][1]+=a;
                              cout<<"total amount in your account :: \t"<<account[match][1];
                          }

}

void bank ::display_balance(int (&account)[r][c])
{

		int i,no,match=10;
							 cout<<"Enter the account number : ";
                             cin>>no;
                             for(i=0;i<5;i++){
                             	if(account[i][0]==no){
                             		match=i;
								 }
							 }
							 if (match==10){
							 	cout<<"No account found ";
							 }
							 else{

							 cout<<"| Account No \t|\t Balance |\n";
                             cout<<account[match][0]<<"\t\t|\t"<<account[match][1];
                         }
}

void bank ::withdraw_money(int (&account)[r][c])
{
    int no,amount,i,match=10;

							 cout<<"Enter the account number : ";
                             cin>>no;
                             for(i=0;i<5;i++){
                             	if(account[i][0]==no){
                             		match=i;
								 }
							 }
							 if (match==10){
							 	cout<<"No account found ";
							 }
							 else{
							 cout<<"\n withdraw :: ";
                             cout<<"enter amount to withdraw :: ";
                             cin>>amount;
                             account[match][1]-=amount;
                             if(account[match][1]<0){
                             	cout<<"!! Insufficient funds !!\n";
                             	account[match][1]+=amount;
							 }
							 else{
                             cout<<"now total amount is left :: "<<account[match][1]<<"\n";
                         	}
                         }

}

int main()
{
    int ch;
    int account[5][2];
    account[0][0]=1001;
    account[1][0]=1002;
    account[2][0]=1003;
    account[3][0]=1004;
    account[4][0]=1005;
    account[0][1]=0;
    account[1][1]=0;
    account[2][1]=0;
    account[3][1]=0;
    account[4][1]=0;
	char x;
    bank obj;
    int count=0;
    do{


	cout<<"\n do you want to select option then press :: y"<<endl;

                           // while(x=='y'||x=='Y');

                            cout<<"if you want to exit then press :: N "<<endl;

                            cin>>x;
    if(x=='n' || x=='N'){

                            cout<<"exit\nThank you!!";\
                            break;
            }
    else
    {


                             cout<<"1) open account\n";
                             cout<<"2) deposit money\n";
                             cout<<"3) withdraw money\n";
                             cout<<"4) display account\n";
                             cout<<"select the option from above \n";
                             cin>>ch;

switch(ch)
 {

          case 1:
                            cout<<"1) open account\n";
                            obj.open_account(account,count);
                            count++;
          break;

          case 2:
                            cout<<"2) deposit money\n";
                            obj.deposit_money(account);
          break;

          case 3:
                            cout<<"3) withdraw money \n";
                            obj.withdraw_money(account);
          break;

          case 4:
                            cout<<"4) display balance \n";
                            obj.display_balance(account);
                            break;

          default:
                            cout<<"this is not exist try  again \n";

 }






    }
}
    while(x=='y'||x=='Y');
return 0;
}
