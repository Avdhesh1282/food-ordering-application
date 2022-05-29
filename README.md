# food-ordering-application
#You have to design a Food Ordering app for a restaurant.   The application will have a log-in for admin and users.   Admin will have the following functionalities:      Add new food items. Food Item will have the following details:     FoodID //It should be generated automatically by the application.     Name     Quantity. For eg, 100ml, 250gm, 4pieces etc     Price     Discount     Stock. Amount left in stock in the restaurant.     Edit food items using FoodID.     View the list of all food items.     Remove a food item from the menu using FoodID.    The user will have the following functionalities:      Register on the application. Following to be entered for registration:     Full Name     Phone Number     Email     Address     Password     Log in to the application     The user will see 3 options:     Place New Order     Order History     Update Profile     Place New Order: The user can place a new order at the restaurant.     Show list of food. The list item should as follows:     1. Tandoori Chicken (4 pieces) [INR 240]     2. Vegan Burger (1 Piece) [INR 320]     3. Truffle Cake (500gm) [INR 900]     Users should be able to select food by entering an array of numbers. For example, if the user wants to order Vegan Burger and Truffle Cake they should enter [2, 3]     Once the items are selected user should see the list of all the items selected. The user will also get an option to place an order.     Order History should show a list of all the previous orders     Update Profile: the user should be able to update their profi
class Restaurant:
    def __init__(self,name,Price,Discount,Orders,Quantity):
        self.name = name
        self.Price= Price
        self.Discount = dict()
        self.orders = []
        self.Quantity={}
        
    def add_menu(self,name,price):
        self.menu.update({name:price})
        
    def print_menu(self):
        for key,value in self.menu.items():
            print(f'{key} ----> {value}')
        
        
        
    def __repr__(self):
        return f'name: {self.name}, Location:{self.add}'

class User:
    def __init__(self,full name, address ,phone number, password):
        self.name = full name
        self.add = address
        self.phone = phone number
        self.pass = Passward
    def __inti__(Login here ,Place order , Order History )
        self.Login= Login here
        self.Order= Place Order
        self.History= Older History
    def __repr__(self):
        return f'name: {self.Update profile}, Location:{self.Rgister in App} Phone:{self.Email}'
        self.Update= Update Profile
        self.Rgister= Rgister in App
        self.Email = Email Address
     
     def print_menu(self,res_name):
        res_name.print_menu()
        
    
    

AVDHESH RAJPUT RESTAURANT MENU = Restaurant('ARR','Raipur')

print(ARR)

name:ARR, Location:Raipur

ARR.add_menu('Tandoori Chicken(4 pieces)',[INR 240])
ARR.add_menu('Vegan Burger (1 piece)',[INR 320])
ARR.add_menu('Truffle Cake (500 gb)',[INr 900])

ARR.print_menu()

Tandoori Chicken (4 pieces)240 ---->
 Vegan Burger (1 pieces) 320----> 
 Truffle Cake(500 gm)900----> 

pritom = User('Pritom','Raipur','323220042')

print(pritom)

name: Pritom, Location:Raipur Phone:323220042

pritom.print_menu(ARR)

Tandoori Chicken (4 pieces)240 ---->
 Vegan Burger (1 pieces) 320----> 
 Truffle Cake(500 gm)900----> 

