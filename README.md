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
