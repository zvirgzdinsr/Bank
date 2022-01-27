# Bank
#Client class
#name
#timestamp (optional)

import datetime

#UZDEVUMS: izveido klasi Transaction
class Transaction:
    def __init__(self, amount: float = 0, note: str = ''):
        self.amount = amount
        self.note = note
        self.timestamp = datetime.datetime.now()

class Account:
    auto_account_number = 1234567890
    
    def __init__(self, currency: str, initial_balance: float = 0):
        self.account_number = Account.auto_account_number
        Account.auto_account_number += 1
        self.currency = currency
        self.initial_balance = initial_balance
        self.timestamp = datetime.datetime.now()

class Client:
    def __init__(self, name: str):
        self.name = name
        self.timestamp = datetime.datetime.now()
        self.accounts = []

    def add_account(self, account: Account):
        self.accounts.append(account)

    def print_accounts(self):
        print(f'Accounts of client {self.name}')
        for account in self.accounts:
            print(f'{account.account_number} ({account.currency} {account.initial_balance})')        

clients = []
clients.append(Client('Anna'))
clients.append(Client('Jenifer'))
clients.append(Client('Miki'))

clients[0].add_account(Account('EUR', 200))
clients[0].add_account(Account('USD', 150))
clients[0].add_account(Account('CAD', 300))

clients[1].add_account(Account('EUR', 800))
clients[1].add_account(Account('JPY', 10000))

clients[2].add_account(Account('EUR'))

clients[0].account_number = '999999999999'


for client in clients:
    client.print_accounts()
