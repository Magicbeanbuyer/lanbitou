db transaction is a single unit of work that are often made up of multiple db operations.  
  
Following five operations composes one db transaction.  
1. create a transaction record of 10 EUR from account1 to account2  
2. create an entry record of -10 EUR for account1  
3. create an entry record of 10 EUR for account2  
4. reduce account1's amount by -10 in their account record  
5. increase account2's amount by 10 in their account record  
  
db transaction must be [[ACID]]  
