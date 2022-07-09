## Unit 19 Homework: Cryptocurrency Wallet

<img width="1197" alt="Screen Shot 2022-07-09 at 4 42 26 PM" src="https://user-images.githubusercontent.com/53786396/178122145-ea9218aa-3b2e-4350-978b-504c7bf5c658.png">

<img width="1194" alt="Screen Shot 2022-07-09 at 4 42 44 PM" src="https://user-images.githubusercontent.com/53786396/178122151-a8d114b5-559d-4f37-8172-7a7487e0b30e.png">

<img width="408" alt="Screen Shot 2022-07-09 at 4 43 19 PM" src="https://user-images.githubusercontent.com/53786396/178122155-4ec84e87-ad98-4707-b041-f404d54d6701.png">

### What You're Creating

* Generate a new Ethereum account instance by using the mnemonic seed phrase provided by Ganache.

* Fetch and display the account balance associated with your Ethereum account address.

* Calculate the total value of an Ethereum transaction, including the gas estimate, that pays a Fintech Finder candidate for their work.

* Digitally sign a transaction that pays a Fintech Finder candidate, and send this transaction to the Ganache blockchain.

* Review the transaction hash code associated with the validated blockchain transaction.

Once you receive the transaction’s hash code, you will navigate to the Transactions section of Ganache to review the blockchain transaction details. To confirm that you have successfully created the transaction, you will save screenshots to the README.md file of your GitHub repository for this Challenge assignment.

### Instructions

The steps for this challenge are broken out into the following sections:

* Import Ethereum Transaction Functions into the Fintech Finder Application
* Sign and Execute a Payment Transaction
* Inspect the Transaction on Ganache

#### Step 1: Import Ethereum Transaction Functions into the Fintech Finder Application

In this section, you'll import several functions from the `crypto_wallet.py` script into the file `fintech_finder.py`, which contains code for Fintech Finder’s customer interface, in order to add wallet operations to the application. For this section, you will assume the perspective of a Fintech Finder customer (i.e., you’ll provide your Ethereum wallet and account information to the application).

Complete the following steps:

1. Review the code contained in the `crypto_wallet.py` script file. Note that the Ethereum transaction functions that you have built throughout this module&mdash;including `wallet`, `wallet.derive_acount`, `get_balance`, `fromWei`, `estimateGas`, `sendRawTransaction`, and others&mdash;have now been incorporated into Python functions that allow you to automate the process of accessing them.

2. Add your mnemonic seed phrase (provided by Ganache) to the starter code’s `SAMPLE.env` file. When the information has been added, rename the file `.env`.

3. Open the `fintech_finder.py` file. Toward the top of the file, after the import statements that are provided, import the following functions from the `crypto_wallet.py` file:

    * `generate_account`

    * `get_balance`

    * `send_transaction`

4. Within the Streamlit sidebar section of code, create a variable named `account`. Set this variable equal to a call on the `generate_account` function. This function will create the Fintech Finder customer’s (in this case, your) HD wallet and Ethereum account.

5. Within this same section of the `fintech_finder.py` file, define a new `st.sidebar.write` function that will display the balance of the customer’s account. Inside this function, call the `get_balance` function and pass it your Ethereum `account.address`.

#### Step 2: Sign and Execute a Payment Transaction

Next, you'll write the code that will calculate a fintech professional’s wage, in ether, based on the worker’s hourly rate and the number of hours that they work for a customer. (The fintech professionals’ hourly rates are provided in the `candidate_database` that is found in `fintech_finder.py`.)

You will then write code that uses the calculated wage value to send a transaction that pays the worker. This code should allow the Fintech Finder customer to authorize the transaction with their digital signature. For the purpose of testing out this application, you will use your own Ethereum account information as the customer account information.

To accomplish all of this, complete the following steps:

1. Fintech Finder customers will select a fintech professional from the application interface’s drop-down menu, and then input the amount of time for which they’ll hire the worker. Code the application so that once a customer completes these steps, the application will calculate the amount that the worker will be paid in ether. To do so, complete the following steps:

    * Write the equation that calculates the candidate’s wage. This equation should assess the candidate’s hourly rate from the candidate database (`candidate_database[person][3]`) and then multiply this hourly rate by the value of the `hours` variable. Save this calculation’s output as a variable named `wage`.

    * Write the `wage` variable to the Streamlit sidebar by using `st.sidebar.write`.

2. Now that the application can calculate a candidate’s wage, write the code that will allow a customer (you, in this case) to send an Ethereum blockchain transaction that pays the hired candidate. To accomplish this, locate the code that reads `if st.sidebar.button("Send Transaction")`. You’ll need to add logic to this `if` statement that sends the appropriate information to the `send_transaction` function (which you imported from the `crypto_wallet` script file). Inside the `if` statement, add the following functionality:

    * Call the `send_transaction` function and pass it three parameters:

    * Your Ethereum `account` information. (Remember that this `account` instance was created when the `generate_account` function was called.) From the `account` instance, the application will be able to access the `account.address` information that is needed to populate the `from` data attribute in the raw transaction.

    * The `candidate_address` (which will be created and identified in the sidebar when a customer selects a candidate). This will populate the `to` data attribute in the raw transaction.

    * The `wage` value. This will be passed to the `toWei` function to determine the wei value of the payment in the raw transaction.

    * Save the transaction hash that the `send_transaction` function returns as a variable named `transaction_hash`, and have it display on the application’s web interface.

#### Step 3: Inspect the Transaction

Now it's time to put it all together and test the Fintech Finder application with your newly integrated Ethereum wallet. You will send a test transaction by using the application’s web interface, and then look up the resulting transaction in Ganache. To do so, complete the following steps:

1. From your terminal, navigate to the project folder that contains your `.env` file and the `fintech_finder.py` and `crypto_wallet.py` files. Be sure to activate your Conda `dev` environment if it is not already active.

2. To launch the Streamlit application, type `streamlit run fintech_finder.py`.

3. On the resulting webpage, select a candidate that you would like to hire from the appropriate drop-down menu. Then, enter the number of hours that you would like to hire them for. (Remember, you do not have a lot of ether in your account, so you cannot hire them for long!)

4. Click the Send Transaction button to sign and send the transaction with your Ethereum account information. Navigate to the Transactions section of Ganache.

    * Take a screenshot of your address balance and history on Ganache. Save this screenshot to the README.md file of your GitHub repository for this Challenge assignment.

    * Take a screenshot of the transaction details on Ganache. Save this screenshot to the README.md file of your GitHub repository for this Challenge assignment.

5. Return to the original transaction, and click the transaction’s To address.

* Take a screenshot of the recipient’s address balance and history from your Ganache application. Save this screenshot to the README.md file of your GitHub repository for this Challenge assignment.

---
