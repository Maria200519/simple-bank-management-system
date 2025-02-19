# simple-bank-management-system
class bank:
    interest_rate=5
    def __init__(self,bank_name):
        self.bank_name=bank_name
        self.customer={}
    def create_account(self,customer_id,name,initial_deposit):
        if customer_id in self.customer:
            print("Account Already Exists!!!")
        else:
            self.customer[customer_id]={"name":name,"balance":initial_deposit}
            print("Account successfully created!!!")
    def deposit(self,customer_id,amt):
        if customer_id in self.customer:
            self.customer[customer_id]["balance"]+=amt
            print("The amount got debited successfully,Your new balance is ",self.customer[customer_id]["balance"])
    def withdraw(self,customer_id,amt):
        if customer_id in self.customer:
            if self.customer[customer_id]["balance"]>=amt:
                self.customer[customer_id]["balance"]-=amt
                print("The amount withdrawn successfully,your new balance is",self.customer[customer_id]["balance"])
            else:
                print("The amount not sufficient!!")
    def display_balance(self,customer_id):
        if customer_id in self.customer:
            balance=self.customer[customer_id]["balance"]
            print("Your current balance is",balance)
    @classmethod
    def update_interest_rate(cls,new_rate):
        cls.interest_rate=new_rate
        print("the updated rate is",new_rate)
    @staticmethod
    def annual_interest(amt):
        annual_interest=amt*bank.interest_rate
        return annual_interest
class premiumbank(bank):
    def bonus(self,customer_id,bonus_amt):
        if customer_id in self.customer:
            self.customer[customer_id]["balance"]+=bonus_amt
            print("Congrats!!You got a bonus of amt",bonus_amt,",so,Your new balance is",self.customer[customer_id]["balance"])
        else:
            print("Account not exist!!")
b_name=input("Enter the bank name:\n")
bank1=bank(b_name)
customer_id=int(input("Enter Your customer_id:\n"))
name=input("Enter your Name:\n")
initial_deposit=int(input("Enter the amount for your first deposit:\n "))
bank1.create_account(customer_id,name,initial_deposit)
amt=int(input("Enter the amount to be deposited:\n"))
bank1.deposit(customer_id,amt)
amt=int(input("Enter the amount to be withdrawn:\n"))
bank1.withdraw(customer_id,amt)
bank1.display_balance(customer_id)
new_rate=int(input("Enter your new interest rate:\n"))
bank.update_interest_rate(new_rate)
amt=int(input("Enter the amount of which the interest has to found:\n"))
annual_inter=bank.annual_interest(amt)
print("the annual interest:",annual_inter)
p_name=input("Enter the name of the premium bank:\n")
p_bank=premiumbank(p_name)
customer_id=int(input("Enter the customer id:\n"))
name=input("Enter the name of the account holder:\n")
deposit=int(input("Enter the amount to be deposited:\n"))
p_bank.create_account(customer_id,name,deposit)
bonus_amt=int(input("Enter the bonus amount to be awarded to the account holder"))
p_bank.bonus(customer_id,bonus_amt)
p_bank.display_balance(customer_id)

