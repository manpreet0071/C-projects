#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void menu();
void diposit();
void withdrawal();
void view();


struct information{
	char name[50];
	char number[20];
	char pin[30];
	char cash[20];
	char date[10];
};


void menu()
{
	int choice ;
	printf("WELCOME TO TRANSITION PAGE.");
	printf("\n\n~Options :- \n\n");
	printf("1. Diposit money. \n");
	printf("2. Withdrawal money. \n");
	printf("3. View Balanace. \n");
	printf("4. Exit. \n");
	
	printf("\nPlease, select an option :-  ");
	scanf("%d",&choice);
	getchar(); // clear input buffer
    system("cls");  // Clears screen (Windows only)

	switch(choice)
	{
		case 1:
			diposit();
			break;
			
		case 2:
		    withdrawal();
		    break;
		    
		case 3:
			view();
			break;
			
		case 4:
		    printf("Exit the page, Good bye.\n");
		    break;
		    
		default:
            printf("Invalid choice. Please try again.\n");
            menu();
            break;  
		    
	}
}
 
void diposit()
{
	struct information user;

	printf("WELCOME! TO THE DIPOSIT SECTION.\n\n");
	
	printf("Enter your name :- ");
	scanf("%s",&user.name);
	printf("Enter your account no. :- ");
	scanf("%s",&user.number);
	printf("Enter your pin :- ");
	scanf("%s",&user.pin);
	printf("Enter the amount of cash :-");
	scanf("%s",&user.cash);
	printf("Enter Date :- ");
	scanf("%s",&user.date);

    int depositAmount = atoi(user.cash);
//    printf("R :-%d\n",newCash);


//      struct accountcreate user ;
    FILE*fptr = fopen("deposit.txt","a");
    if (fptr==NULL){
    ("error in file opening \n");
    }
 
 
    fprintf(fptr, "--------------------------\n");
    fprintf(fptr, "Name                :- %s\n", user.name);
	fprintf(fptr, "Account number      :- %s\n", user.number);
	fprintf(fptr, "Password/Pin        :- %s\n", user.pin);
	fprintf(fptr, "Cash Amount         :- %s\n", user.cash);
	fprintf(fptr, "Date                :- %s\n", user.date);
//	fprintf(fptr, "R cash              :- %d\n", newCash);
    fprintf(fptr, "--------------------------\n");
	fclose(fptr);



    FILE *fbal = fopen("balance.txt", "r+");
    int balance = 0;
    if (fbal != NULL) {
        fscanf(fbal, "%d", &balance);
        rewind(fbal);
    } else {
        fbal = fopen("balance.txt", "w");
    }
    balance += depositAmount;
//    fprintf(fbal, "%d", balance);
	fprintf(fbal, "New Balance         :- %s\n", user.cash);
    fclose(fbal);

    printf("\nDeposited: %d\n", depositAmount);
    printf("New Balance: %d\n", balance);
    printf("Thank you!\n\n");



	view();
	
   };
    



void withdrawal()
{
	struct information user;
	
	printf(" WELCOME! TO THE WITHDRAWAL SECTION.\n\n");
	
	printf("Enter your name :- ");
	scanf("%s",&user.name);
	printf("Enter your account no. :- ");
	scanf("%s",&user.number);
	printf("Enter your pin :- ");
	scanf("%s",&user.pin);
	printf("Enter the amount of cash :-");
	scanf("%s",&user.cash);
	printf("Enter Date :- ");
	scanf("%s",&user.date);
	fflush(stdin);

//      struct accountcreate user ;
 
	
	int withdrawalAmount = atoi(user.cash);
//	printf("\nYour %s rupess amount has been succesfuly withdrawal. Thanks!\n\n",user.cash);
//	printf("Now you can go to check the your balance.");
//	menu();
    
    FILE *fbal = fopen("balance.txt", "r+");
    int balance = 0 ;
    if(fbal == NULL){
    	printf("No existing balance found.\n");
    	return ;
	}
	fscanf(fbal, "%d", & balance );
    if(withdrawalAmount > balance){
    	printf("Insufficant Balanace!,  Transition canceled.");
    	fclose(fbal);
    	return;
	}

    
    rewind(fbal);
    balance -= withdrawalAmount;
    fprintf(fbal, "%d", balance);
    fclose(fbal);

    // Record withdrawal
    FILE *fptr = fopen("deposit.txt", "a");
    if (fptr == NULL) {
        printf("Error opening transaction file.\n");
        return;
    }

 
    fprintf(fptr, "--------------------------\n");
    fprintf(fptr, "Name                :- %s\n", user.name);
	fprintf(fptr, "Account number      :- %s\n", user.number);
	fprintf(fptr, "Password/Pin        :- %s\n", user.pin);
	fprintf(fptr, "Cash Amount         :- %s\n", user.cash);
	fprintf(fptr, "Date                :- %s\n", user.date);
    fprintf(fptr, "--------------------------\n");
	fclose(fptr);
	
	
    printf("\nWithdrawn: %d\n", withdrawalAmount);
    printf("New Balance: %d\n\n", balance);

    menu();



}


int main()
{
	menu();
	return 0;
}
  

// Function 3: view
void view() {
    FILE *fbal = fopen("balance.txt", "r");
    int balance = 0;

    printf("\n~ View Balance Page ~\n");

    if (fbal == NULL) {
        printf("No balance found. Make a deposit first.\n\n");
    } else {
        fscanf(fbal, "%d", &balance);
        printf("Your current balance is:- %d\n\n", balance);
        fclose(fbal);
    }

    menu();
}

