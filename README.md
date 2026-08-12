# Bank-Management-System
A Python-based ATM Simulation Management System that provides secure PIN login, balance checking, deposits, withdrawals, transaction history, and PIN management.
from dataclasses import dataclass
class AccountNotFoundError(Exception):
    pass
class InsufficientFundsError(Exception):
    pass
class AccountAlreadyExistsError(Exception):
    pass
class InvalidAmountError(Exception):
    pass
class AccountClosedError(Exception):
    pass
@dataclass
class Account:
    id: int
    customer_name: str
    balance: float = 0.0
accounts = {}
next_id = 1
def get_account(account_id):
    if account_id not in accounts:
        raise AccountNotFoundError("Account not found.")
    return accounts[account_id]
def create_account(customer_name):
    global next_id
    account = Account(next_id, customer_name, 0.0)
    accounts[next_id] = account
    print("Account created successfully!")
    print("Account ID:", next_id)
    next_id += 1
def deposit(account_id, amount):
    account = get_account(account_id)
    if amount <= 0:
        raise InvalidAmountError(
            "Deposit amount must be greater than zero."
        )
    account.balance += amount
    print("Deposit successful.")
    print("Current balance: ₹", account.balance)
def withdraw(account_id, amount):
    account = get_account(account_id)
    if amount <= 0:
        raise InvalidAmountError(
            "Withdrawal amount must be greater than zero."
        )
    if amount > account.balance:
        raise InsufficientFundsError("Insufficient funds.")
    account.balance -= amount
    print("Withdrawal successful.")
    print("Current balance: ₹", account.balance)
