```python
#dictionary with 5 default products
products = [
    {"name":"sal","quantity":"100","price":"2550"},
    {"name":"bocadillo","quantity":"200","price":"4990"},
    {"name":"galletas","quantity":"150","price":"6250"},
    {"name":"desodorante","quantity":"50","price":"4490"},
    {"name":"electrolit","quantity":"250","price":"8700"},
]
def register(): #function to register products
  print ("\n---Register a new product---")
  name = input("Enter product name ").strip()
  try: #If an invalid value is entered, it will display an error.
     quantity = int(input("Enter the quantity of products "))
     if quantity < 0: #tests whether the quantity is a positive integer
        print("Invalid quantity. Please enter a valid quantity")
        return
  except ValueError:
     print("Invalid input. quantity must be a number. ")
  try: #If an invalid value is entered, it will display an error.
     price = float(input("Enter price: "))
     if price <= 0:  #validates that the entered value is a positive decimal
        print("Invalid price. Price must be a positive number")
        return
  except ValueError:
     print("Invalid input. price must be a number. ")
  for product in products: #Validates if the entered name already appears in the inventory, in which case it will display a message
      if product['name'].lower() == name.lower():
          print(" product already exist in the inventory. ")
          return
  new_product = { #add the product to the dictionary
      "name": name,
      "quantity": quantity,
      "price": round(price,2)
  }    
  products.append(new_product) #shows that the product has already been registered
  print(f"\nProduct'{name}'registered successfully. ")
  main()
def search(): #function to search for a product
   print("\n---Search Product---")
   ask = input("Enter product name to search: ").strip().lower()
   found = False
   for product in products: #Request the product name, if the name appears in the dictionary keys, it will display the product information
      if ask in product['name'].lower():
         print(f"\nProduct found: \n"
               f"name: {product['name']}\n"
               f"Quantity available: {product['quantity']}\n"
               f"Price: ${product['price']}\n")
         found = True
   if not found: #If the product does not exist, ask if the user wants to register it.
      print("product not found. Do you want to register it? (yes/No)")
      answer = input().strip().lower()
      if answer == "yes":
         register()
      elif answer == "no":
         main()
   main()
def update(): #the same search function for a product, and then gives the option to update the product price
   print("\n---Search Product---")
   ask = input("Enter product name to search: ").strip().lower()
   found = False
   for product in products:
      if ask in product['name'].lower():
         print(f"\nProduct found: \n"
               f"name: {product['title']}\n"
               f"Quantity available: {product['quantity']}\n"
               f"Price: ${product['price']}\n")
         found = True
         data_change = input("Which value you want to change: ") #Validate what information you want to update, price or quantity
         if data_change in products.keys():
            new_value = input("What value do you want to change it to?").strip()
            if data_change in ['quantity']:
               try:
                  new_value = int(new_value)
               except ValueError:
                  print("Error: value must be a number")
                  return
            elif data_change == 'price':
               try:
                  new_value = float(new_value)
               except ValueError:
                  print("Error: value must be a decimal number.")
                  return
            product[data_change] = new_value
            print(f"{data_change.capitalize()} has been updated successfully.\n")
         else:
            print("This value cant be changed!")
         break
   if not found: #creates a variable "found" if this is false, it shows whether you want to register the product
      print("Product not found. Do you want to register it? (yes/No)")
      answer = input().strip().lower()
      if answer == "yes":
         register()
      elif answer == "no":
         main()        
def delete(): #function to delete products
   print("\n---Delete Product---")
   delete = input("Enter product name to delete: ").strip().lower()
   found = False
   if delete in products: #look up if the product is in the dictionary,
      answer = print("Are you sure to delete this product? (yes/no) \n") #asks if he wants to delete the product
      if answer =="yes":
         del products[delete]
         print("product successfully deleted.")
      else:
         print("Deletion cancelled")
   else:
      print("product not found.")
def generate(): #function to generate the inventory report
   try:
     action = str(input("Do you want to see inventory report?: (yes/no)\n")).strip().lower()
     if action == "no":
        main()
     elif action == "yes":
        print("\n---Report inventory---")
        total_cost = 0
        for product in products.values():
           cost =product['quantity'] * product['price']
           total_cost += cost
           print(f"{product['name']} - {product['quantity']} units - $ {cost}")
        print(f"Total inventory price: ${total_cost}") #Displays the inventory and price report
   except ValueError: #if an invalid value is entered it displays an error
     print("invalid value, must be (yes/no)") 
def main (): #main menu function
    while True:
        print("\n ---Options menu---")
        print("1. Register new products")
        print("2. Search product")
        print("3. Update information")
        print("4. Delete product")
        print("5. generate inventory report")
        print("6. Exit")
        opcion = input("Choose an option (1-6): ")
    #calls the other functions
        if opcion == "1":
            register()
        elif opcion == "2":
            search()
        elif opcion == "3":
            update()
        elif opcion == "4":
            delete()
        elif opcion == "5":
            generate()    
        elif opcion == "6":
            print("see you later! ")
        break
    else:
        print("invalid option try again.\n")

main()
```
```python
# Dictionary with 5 default products
products = [
    {"name": "sal", "quantity": 100, "price": 2550},
    {"name": "bocadillo", "quantity": 200, "price": 4990},
    {"name": "galletas", "quantity": 150, "price": 6250},
    {"name": "desodorante", "quantity": 50, "price": 4490},
    {"name": "electrolit", "quantity": 250, "price": 8700},
]

def register():
    # Function to register a new product
    print("\n---Register a new product---")
    name = input("Enter product name: ").strip()
    
    try:
        quantity = int(input("Enter the quantity of products: "))
        if quantity < 0:
            print("Invalid quantity. Please enter a valid quantity.")
            return
    except ValueError:
        print("Invalid input. Quantity must be a number.")
        return

    try:
        price = float(input("Enter price: "))
        if price <= 0:
            print("Invalid price. Price must be a positive number.")
            return
    except ValueError:
        print("Invalid input. Price must be a number.")
        return

    for product in products:
        if product['name'].lower() == name.lower():
            print("Product already exists in the inventory.")
            return

    # Add the new product to the list
    new_product = {
        "name": name,
        "quantity": quantity,
        "price": round(price, 2)
    }
    products.append(new_product)
    print(f"\nProduct '{name}' registered successfully.")
    main()

def search():
    # Function to search a product by name
    print("\n---Search Product---")
    ask = input("Enter product name to search: ").strip().lower()
    found = False

    for product in products:
        if ask in product['name'].lower():
            print(f"\nProduct found:\n"
                  f"Name: {product['name']}\n"
                  f"Quantity available: {product['quantity']}\n"
                  f"Price: ${product['price']}\n")
            found = True

    if not found:
        print("Product not found. Do you want to register it? (yes/no)")
        answer = input().strip().lower()
        if answer == "yes":
            register()
        elif answer == "no":
            main()
    else:
        main()

def update():
    # Function to update a product's price or quantity
    print("\n---Update Product---")
    ask = input("Enter product name to search: ").strip().lower()
    found = False

    for product in products:
        if ask in product['name'].lower():
            print(f"\nProduct found:\n"
                  f"Name: {product['name']}\n"
                  f"Quantity available: {product['quantity']}\n"
                  f"Price: ${product['price']}\n")
            found = True

            data_change = input("Which value do you want to change (quantity/price)? ").strip().lower()
            if data_change in product:
                new_value = input("What value do you want to change it to? ").strip()
                if data_change == 'quantity':
                    try:
                        new_value = int(new_value)
                    except ValueError:
                        print("Error: value must be a number.")
                        return
                elif data_change == 'price':
                    try:
                        new_value = float(new_value)
                    except ValueError:
                        print("Error: value must be a decimal number.")
                        return
                product[data_change] = new_value
                print(f"{data_change.capitalize()} has been updated successfully.\n")
            else:
                print("This value can't be changed!")
            break

    if not found:
        print("Product not found. Do you want to register it? (yes/no)")
        answer = input().strip().lower()
        if answer == "yes":
            register()
        elif answer == "no":
            main()
    else:
        main()

def delete():
    # Function to delete a product by name
    print("\n---Delete Product---")
    name_to_delete = input("Enter product name to delete: ").strip().lower()
    found = False

    for product in products:
        if name_to_delete == product['name'].lower():
            found = True
            confirm = input("Are you sure you want to delete this product? (yes/no): ").strip().lower()
            if confirm == "yes":
                products.remove(product)
                print("Product successfully deleted.")
            else:
                print("Deletion cancelled.")
            break

    if not found:
        print("Product not found.")
    main()

def generate():
    # Function to generate an inventory report
    try:
        action = input("Do you want to see inventory report? (yes/no): ").strip().lower()
        if action == "no":
            main()
        elif action == "yes":
            print("\n---Inventory Report---")
            total_cost = 0
            for product in products:
                cost = product['quantity'] * product['price']
                total_cost += cost
                print(f"{product['name']} - {product['quantity']} units - $ {cost}")
            print(f"Total inventory value: ${total_cost}")
    except ValueError:
        print("Invalid value. Must be (yes/no)")
    main()

def main():
    # Main menu function
    while True:
        print("\n---Options Menu---")
        print("1. Register new products")
        print("2. Search product")
        print("3. Update information")
        print("4. Delete product")
        print("5. Generate inventory report")
        print("6. Exit")

        option = input("Choose an option (1-6): ")

        if option == "1":
            register()
        elif option == "2":
            search()
        elif option == "3":
            update()
        elif option == "4":
            delete()
        elif option == "5":
            generate()
        elif option == "6":
            print("See you later!")
            break
        else:
            print("Invalid option. Try again.")

main()
```
