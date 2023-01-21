from datetime import date
#Functions
class Menu :
    shop= "Food Plaza"
    password= "Animesh@123"
    
    def __init__(self, food, price):
        self.food= food
        self.price= price
        
    def __str__(self):
        print( f"\n\n\t ===== {Menu.shop} ===== ")
        print("\n\t ITEM \t\tPRICE")
        for i in range(len(self.food)):
            if len(self.food[i])< 11 and (i+1)<10:
                print( f"  {i+1}. {self.food[i]}\t\tRs. {self.price[i]}/-")
            else:
                print( f"  {i+1}. {self.food[i]}\tRs. {self.price[i]}/-")
        return "\n\t≈≈Let's plan your breakfast≈≈"
    
    def __add__(self, addMenu):
        for item in addMenu.food:
            self.food.append(item)
        for value in addMenu.price:
            self.price.append(value)
        return Menu(self.food, self.price)
        
    def addItem(self, item, value):
        self.food.append(item)
        self.price.append(value)
        return Menu(self.food, self.price)
        
    def removeItem(self, num):
        self.food.pop(num-1)
        self.price.pop(num-1)
        return Menu(self.food, self.price)
    
    @classmethod  
    def changeShop(cls,shopName):
        cls.shop= shopName
        
    @classmethod
    def changePassword(cls, newPassword):
        cls.password= newPassword
        
    def greet(self, name):
        print(f"\n\nHello, {name}")
        print(f"Welcome to {self.shop}")
        
    def changePrice(self, num, newValue):
        self.price.pop(num-1)
        self.price.insert(num-1, newValue)
        return Menu(self.food, self.price)
    
    
class Order(Menu):
    
    def __init__(self, food, price, order, count):
        super().__init__(food, price)
        self.order= order
        self.count= count
        
    def __str__(self):
        print(f"\n\n\t{name}'s order: ")
        print("\n    ITEM \t\t QUANTITY")
        for i in range(len(self.order)):
            if len(self.food[self.order[i]-1])<12 :
                print(f"{i+1}. {self.food[self.order[i]-1]} \t\t {self.count[i]}")
            else:
                print(f"{i+1}. {self.food[self.order[i]-1]} \t {self.count[i]}")
        return "\n\t please wait...."
        
    def showBill(self):
        print(f"\n\n\t===== {self.shop} =====")
        print(f"\n Name: {name}")
        print(" Date: " , date.today())
        print(f"\n    ITEM \t\t QUANTITY \t PRICE")
        sum=0
        for i in range(len(self.order)):
            value= self.price[self.order[i]-1]* self.count[i]
            if len(self.food[self.order[i]-1]) <12:
                print(f"{i+1}. {self.food[self.order[i]-1]} \t\t {self.count[i]} \t\t {value}")
            else:
                print(f"{i+1}. {self.food[self.order[i]-1]} \t {self.count[i]} \t\t {value}")
            sum += value
        print( f"\tTotal: Rs.{sum}/-")
        
    def addOrder(self, newOrder, newCount):
        self.order.append(newOrder)
        self.count.append(newCount)
        return Order(self.food, self.price, self.order,self.count)
        
    def removeOrder(self, num):
        self.order.pop(num-1)
        self.count.pop(num-1)
        return Order(self.food, self.price, self.order, self.count)
        
    def changeCount(self, num, newQuantity):
        self.count.pop(num-1)
        self.count.insert(num-1, newQuantity)
        return Order(self.food, self.price, self.order, self.count)
        
    def cancelOrder(self):
        self.order=[]
        self.count=[]
        return Order(self.food, self.price, self.order, self.count)

#Base
food=["Egg Biriyani", "Alu Biriyani", "Chicken Biriyani", "Motton Biriyani", "Egg Chowmin", "Chicken Chowmin", "Dhaveli", "Eggroll", "Chicken Roll", "Vegitable soup", "Chicken soup"]
price= [75, 60, 90, 120, 50, 70, 20, 35, 50, 40, 80]
menu= Menu(food, price)
order=[]
count=[]
yourOrder= Order(food, price, order, count)

#structure
try :
    name= input("Enter your name: ")
    menu.greet(name)
    while(1):
        print('''
    1. See Menu
    2. Order
    3. Check Bill
    4. Management Authority
    0. Exit
    ''')
        a= int(input("Choose option: "))
        
        if (a==0): #Exit
            print("Bye!, please come again...")
            exit()
        
        elif(a==1): #See Menu
            print(menu)
        
        elif(a==2): #Order
            print('''
        1. Give Order
        2. View your Order
        3. Add an Item
        4. Remove an Item
        5. Change quantity of an Item from given order
        6. Cancel full Order
        ''')
            b= int(input("Choose option: "))
            
            if (b==1): #Give Order
                print(f"\nInstruction:- For giving order enter item idex \n \t\t ex: for {food[2]} enter '3' \n\t\t And enter no. of plate you want to order \n\t\t for done press 'q' ")
                while(1):
                    o= input("Choose item : ")
                    if (o== 'q'):
                        print("\tplease wait.. The order will deliver soon..")
                        break
                    order.append(int(o))
                    count.append(int(input("Enter quantity of this item: ")))
                
            elif (b==2): #View Order
                print(yourOrder)
            
            elif (b==3): #Add Order
                o= int(input("Enter the Item index: "))
                c= int(input("Enter quantity of the Item: "))
                yourOrder.addOrder(o, c)
            
            elif (b==4): #Remove Order
                num= int(input("Please View your current order...\n then enter the index(given in your order) of that item: "))
                yourOrder.removeOrder(num)
            
            elif(b==5): #Changing quantity of item
                num= int(input("Enter the index(from your given order) of that item: "))
                newQuantity= int(input("Enter the new quantity: "))
                yourOrder.changeCount(num, newQuantity)
            
            elif(b==6): #Cancel full order
                print("Are you really want to cancel your order? \n 1. Yes\n 2. No ")
                e=int(input("Enter your choice: "))
                if e==1:
                    yourOrder.cancelOrder()
                elif e==2:
                    print("please wait..\n your order will deliver soon..")
                else:
                    print("Enter a valid option!!")
            
            else:
                print("please choose from given options!! ")
            
        elif (a==3): #show Bill
            yourOrder.showBill()
        
        elif(a==4): #Owner 
            password= input("Enter password: ")
            if (password== Menu.password):
                print(f"welcome! {name}\n Now you can  make changes in shop...")
                while(1):
                    print('''
        1. Change Menu
        2. Change your shopname
        3. Change password
        0. Exit
        ''')
                    c= int(input("Choose an option: "))
                    
                    if (c==1): #Change Menu
                        print('''
                1. Add an Item
                2. Remove an Item
                3. Change price of an Item
                4. Add a newMenu
                ''')
                        d= int(input("Choose an option: "))
                        if(d==1): #add an item
                            item= input("Enter the item name: ")
                            value= int(input("Enter the price of this item: "))
                            menu.addItem(item, value)
                            
                        elif(d==2): #remove an item
                            num= int(input("Enter the index of item from menu which you want to remove: "))
                            menu.removeItem(num)
                            
                        elif(d==3): #change price of an item
                            num= int(input("Enter the index of item from menu: "))
                            newPrice= int(input("Enter the new price of the item: "))
                            menu.changePrice(num, newPrice)
                            
                        elif(d==4): #add a menu
                            print('''
                1. Clear the old menu and add
                2. Add many items with the old one
                3. Cancel
                ''')
                            f= int(input("Choose an option: "))
                            if (f==1 or f==2):
                                if (f==1):
                                    food=[]
                                    price=[]
                                while(1):
                                    f2= input("Enter the item names(press 'd' for done): ")
                                    if (f2=='d'):
                                        break
                                    p2= int(input("Enter the prices: "))
                                    menu.addItem(f2, p2)
                            elif(f==3):
                                pass
                            else:
                                print("Enter a valid option!!")
                            
                        else:
                            print("Enter a valid option!!")
                        
                    elif (c==2): #Change Shopname
                        shopname= input("Enter new shopname: ")
                        menu.changeShop(shopname)
                        
                    elif (c==3): #Change Password
                        password= input("Enter new password: ")
                        menu.changePassword(password)
                        
                    elif (c==0): #Exit from Management Authority
                        break
                    
            else: #wrong password
                print("Wrong Password!!")
                
        else: 
            print("Choose a valid option!!")
            
except Exception as e:
    print(e)
