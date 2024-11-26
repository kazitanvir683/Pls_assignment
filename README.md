# Pls_assignment


ATM System Management

C Program: 


#include <stdio.h> 

// Function declarations 

void checkBalance(double balance); 

void deposit(double *balance); 
void withdraw(double *balance); 
int main() { 
 double balance = 0.0; // Initial balance 
 int choice; 
 int pin = 1234; // Hardcoded PIN for simplicity 
 int enteredPin; 
 // ATM System: PIN Verification 
 printf("Enter your PIN: "); 
 scanf("%d", &enteredPin); 
 if (enteredPin != pin) { 
 printf("Incorrect PIN. Access Denied.\n"); 
 return 0; // Exit the program if PIN is incorrect 
 } 
 // ATM Menu
 do { 
 printf("\n*** ATM Menu ***\n"); 
 printf("1. Check Balance\n"); 
 printf("2. Deposit Money\n"); 
 printf("3. Withdraw Money\n"); 
 printf("4. Exit\n"); 
 printf("Please select an option (1-4): "); 
 scanf("%d", &choice); 
 switch (choice) { 
 case 1: 
 checkBalance(balance); 
 break; 
 case 2: 
 deposit(&balance); 
 break; 
 case 3: 
 withdraw(&balance); 
 break; 
 case 4: 
 printf("Thank you for using the ATM. Goodbye!\n");  break; 
 default: 
 printf("Invalid choice. Please try again.\n");  } 
 } while (choice != 4);
 return 0; 
} 
// Function to check account balance 
void checkBalance(double balance) { 
 printf("Your current balance is: $%.2lf\n", balance); 
} 
// Function to deposit money 
void deposit(double *balance) { 
 double amount; 
 printf("Enter amount to deposit: $"); 
 scanf("%lf", &amount); 
 if (amount > 0) { 
 *balance += amount; 
 printf("Deposited $%.2lf. Your new balance is: $%.2lf\n", amount, *balance);  } else { 
 printf("Invalid deposit amount.\n"); 
 } 
} 
// Function to withdraw money 
void withdraw(double *balance) { 
 double amount; 
 printf("Enter amount to withdraw: $"); 
 scanf("%lf", &amount);
 if (amount <= 0) { 
 printf("Invalid withdrawal amount.\n"); 
 } else if (amount > *balance) { 
 printf("Insufficient funds. Your balance is: $%.2lf\n", *balance);  } else { 
 *balance -= amount; 
 printf("Withdrew $%.2lf. Your new balance is: $%.2lf\n", amount, *balance);  } 
} 






Javascript Program: 



<!DOCTYPE html> 
<html lang="en"> 
<head> 
 <meta charset="UTF-8"> 
 <meta name="viewport" content="width=device-width, initial-scale=1.0">  <title>Simple ATM System</title>
 <style> 
 body { 
 font-family: Arial, sans-serif;  padding: 20px; 
 } 
 .container { 
 max-width: 400px; 
 margin: 0 auto; 
 padding: 20px; 
 border: 1px solid #ccc;  border-radius: 10px;  } 
 .container h2 { 
 text-align: center; 
 } 
 .btn { 
 padding: 10px; 
 margin: 10px; 
 width: 100%; 
 background-color: #4CAF50;  color: white; 
 border: none; 
 cursor: pointer; 
 border-radius: 5px; 
 } 
 .btn:hover { 
 background-color: #45a049;
 } 
 .error { 
 color: red; 
 } 
 .info { 
 color: green; 
 } 
 </style> 
</head> 
<body> 
 <div class="container"> 
 <h2>Simple ATM System</h2> 
 <div id="atm-container"> 
 <label for="pin">Enter your PIN:</label> 
 <input type="password" id="pin" placeholder="Enter PIN" required>  <button class="btn" onclick="login()">Login</button> 
 <p id="login-error" class="error"></p> 
 </div> 
 <div id="atm-menu" style="display:none;"> 
 <p id="balance-display"></p> 
 <button class="btn" onclick="checkBalance()">Check Balance</button>  <button class="btn" onclick="depositMoney()">Deposit Money</button>  <button class="btn" onclick="withdrawMoney()">Withdraw Money</button>  <button class="btn" onclick="logout()">Logout</button>  </div>
 </div> 
 <script> 
 let balance = 0; // Initial balance 
 const pinCode = "1234"; // Hardcoded PIN for simplicity 
 // Function to login and validate the PIN 
 function login() { 
 const enteredPin = document.getElementById("pin").value;  const loginError = document.getElementById("login-error"); 
 if (enteredPin === pinCode) { 
 // Hide login and show ATM menu 
 document.getElementById("atm-container").style.display = "none";  document.getElementById("atm-menu").style.display = "block";  updateBalanceDisplay(); 
 } else { 
 loginError.textContent = "Incorrect PIN. Please try again.";  } 
 } 
 // Function to display the current balance 
 function updateBalanceDisplay() { 
 document.getElementById("balance-display").textContent = `Current Balance:  $${balance.toFixed(2)}`; 
 }
 // Function to check balance 
 function checkBalance() { 
 updateBalanceDisplay(); 
 } 
 // Function to deposit money 
 function depositMoney() { 
 const amount = parseFloat(prompt("Enter amount to deposit:"));  if (amount > 0) { 
 balance += amount; 
 updateBalanceDisplay(); 
 alert(`You have successfully deposited $${amount.toFixed(2)}.`);  } else { 
 alert("Invalid deposit amount."); 
 } 
 } 
 // Function to withdraw money 
 function withdrawMoney() { 
 const amount = parseFloat(prompt("Enter amount to withdraw:"));  if (amount <= 0) { 
 alert("Invalid withdrawal amount."); 
 } else if (amount > balance) { 
 alert("Insufficient balance."); 
 } else { 
 balance -= amount; 
 updateBalanceDisplay();
 alert(`You have successfully withdrawn $${amount.toFixed(2)}.`);  } 
 } 
 // Function to logout and reset the system 
 function logout() { 
 balance = 0; // Reset balance 
 document.getElementById("atm-container").style.display = "block"; // Show login  document.getElementById("atm-menu").style.display = "none"; // Hide ATM menu  document.getElementById("pin").value = ""; // Clear PIN input  } 
 </script> 
</body> 
</html>
