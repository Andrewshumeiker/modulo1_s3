```python
#dictionary with 5 default products
products = [
    {"name":"sal","quantity":"100","price":"2550"},
    {"name":"bocadillo","quantity":"200","price":"4990"},
    {"name":"galletas","quantity":"150","price":"6250"},
    {"name":"desodorante","quantity":"50","price":"4490"},
    {"name":"electrolit","quantity":"250","price":"8700"},
]
def register():
    print("\n--- Register a new product ---")
    name = input("Enter product name: ").strip()
    if not name:
        print("Product name cannot be empty.")
        return

    # Validate quantity
    try:
        quantity_input = input("Enter the quantity of products: ").strip()
        if not quantity_input:
            raise ValueError
        quantity = int(quantity_input)
        if quantity <= 0:
            print("Quantity must be a positive number.")
            return
    except ValueError:
        print("Invalid input. Quantity must be a positive number.")
        return

    # Validate price
    try:
        price_input = input("Enter price: ").strip()
        if not price_input:
            raise ValueError
        price = float(price_input)
        if price <= 0:
            print("Price must be greater than zero.")
            return
    except ValueError:
        print("Invalid input. Price must be a decimal number.")
        return

    # Duplicate name check
    for product in products:
        if product['name'].lower() == name.lower():
            print("Product already exists in the inventory.")
            return

    new_product = {
        "name": name,
        "quantity": quantity,
        "price": round(price, 2)
    }
    products.append(new_product)
    print(f"\nProduct '{name}' registered successfully.")
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
def generate():
    print("\n--- Inventory Report ---")
    action = input("Do you want to see inventory report? (yes/no): ").strip().lower()
    if action not in ["yes", "no"]:
        print("Invalid response. Please enter 'yes' or 'no'.")
        return

    if action == "no":
        return

    total_cost = 0
    for product in products:
        cost = product['quantity'] * product['price']
        total_cost += cost
        print(f"{product['name']} - {product['quantity']} units - ${cost:.2f}")

    print(f"Total inventory value: ${total_cost:.2f}")
def main():
    while True:
        print("\n--- Options Menu ---")
        print("1. Register new products")
        print("2. Search product")
        print("3. Update information")
# Inventory system for managing store products using Python

# Initial list with 5 default products
products = [
    {"name": "salt", "quantity": 100, "price": 2550.00},
    {"name": "guava candy", "quantity": 200, "price": 4990.00},
    {"name": "cookies", "quantity": 150, "price": 6250.00},
    {"name": "deodorant", "quantity": 50, "price": 4490.00},
    {"name": "electrolyte", "quantity": 250, "price": 8700.00},
]

def register():
    print("\n--- Register a new product ---")
    name = input("Enter product name: ").strip()
    if not name:
        print("Invalid input. Product name cannot be empty.")
        return

    try:
        quantity = int(input("Enter the quantity: "))
        if quantity < 0:
            print("Invalid input. Quantity must be a positive number.")
            return
    except ValueError:
        print("Invalid input. Quantity must be a number.")
        return

    try:
        price = float(input("Enter the price: "))
        if price <= 0:
            print("Invalid input. Price must be a positive number.")
            return
    except ValueError:
        print("Invalid input. Price must be a decimal number.")
        return

    for product in products:
        if product['name'].lower() == name.lower():
            print("Product already exists in the inventory.")
            return

    new_product = {"name": name, "quantity": quantity, "price": round(price, 2)}
    products.append(new_product)
    print(f"Product '{name}' registered successfully.")

def search():
    print("\n--- Search Product ---")
    name = input("Enter product name to search: ").strip().lower()
    if not name:
        print("Invalid input. Name cannot be empty.")
        return

    found = False
    for product in products:
        if name in product['name'].lower():
            print(f"\nProduct found:\nName: {product['name']}\nQuantity: {product['quantity']}\nPrice: ${product['price']:.2f}")
            found = True
    if not found:
        print("Product not found.")
        choice = input("Do you want to register it? (yes/no): ").strip().lower()
        if choice == "yes":
            register()

def update():
    print("\n--- Update Product ---")
    name = input("Enter product name to update: ").strip().lower()
    if not name:
        print("Invalid input. Name cannot be empty.")
        return

    found = False
    for product in products:
        if name == product['name'].lower():
            found = True
            print(f"\nProduct found:\nName: {product['name']}\nQuantity: {product['quantity']}\nPrice: ${product['price']:.2f}")
            field = input("Enter field to update (price or quantity): ").strip().lower()

            if field not in ['price', 'quantity']:
                print("Invalid field. Only 'price' or 'quantity' can be updated.")
                return

            new_value = input(f"Enter new value for {field}: ").strip()
            if not new_value:
                print("Invalid input. Value cannot be empty.")
                return

            if field == "quantity":
                try:
                    new_value = int(new_value)
                    if new_value < 0:
                        print("Invalid quantity. Must be a positive number.")
                        return
                except ValueError:
                    print("Invalid input. Quantity must be a number.")
                    return
            elif field == "price":
                try:
                    new_value = float(new_value)
                    if new_value <= 0:
                        print("Invalid price. Must be a positive decimal number.")
                        return
                except ValueError:
                    print("Invalid input. Price must be a decimal number.")
                    return

            product[field] = new_value
            print(f"{field.capitalize()} updated successfully.")
            return
    if not found:
        print("Product not found.")

def delete():
    print("\n--- Delete Product ---")
    name = input("Enter product name to delete: ").strip().lower()
    if not name:
        print("Invalid input. Name cannot be empty.")
        return

    for i, product in enumerate(products):
        if product['name'].lower() == name:
            confirm = input("Are you sure you want to delete this product? (yes/no): ").strip().lower()
            if confirm == "yes":
                del products[i]
                print("Product deleted successfully.")
                return
            else:
                print("Deletion canceled.")
                return
    print("Product not found.")

def generate():
    print("\n--- Inventory Report ---")
    total = 0
    for product in products:
        item_total = product['quantity'] * product['price']
        total += item_total
        print(f"{product['name']} - {product['quantity']} units - ${item_total:.2f}")
    print(f"Total inventory value: ${total:.2f}")

def main():
    while True:
        print("\n--- Inventory Menu ---")
        print("1. Register new product")
        print("2. Search product")
        print("3. Update product")
        print("4. Delete product")
        print("5. Generate inventory report")
        print("6. Exit")

        option = input("Choose an option (1-6): ").strip()
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
            print("Goodbye!")
            break
        else:
            print("Invalid option. Please choose a number between 1 and 6.")

main()
        print("4. Delete product")
        print("5. Generate inventory report")
        print("6. Exit")
        
        opcion = input("Choose an option (1-6): ").strip()
        
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
            print("See you later!")
            break
        else:
            print("Invalid option. Please enter a number between 1 and 6.")
main()

```
```python
def update():
    name = input("Enter the product name to update: ")
    for product in products:
        if product['name'].lower() == name.lower():
            field = input("What do you want to update? (price/quantity): ").lower()
            if field == 'price':
                try:
                    new_price = float(input("Enter the new price: "))
                    if new_price <= 0:
                        print("Price must be a positive number.")
                        return
                    product['price'] = new_price
                    print(f"Price updated successfully to {new_price}.")
                except ValueError:
                    print("Invalid price.")
                return
            elif field == 'quantity':
                try:
                    new_quantity = int(input("Enter the new quantity: "))
                    if new_quantity < 0:
                        print("Quantity must be zero or a positive number.")
                        return
                    product['quantity'] = new_quantity
                    print(f"Quantity updated successfully to {new_quantity}.")
                except ValueError:
                    print("Invalid quantity.")
                return
            else:
                print("Invalid option. Choose 'price' or 'quantity'.")
                return
    print(f"Product '{name}' not found in inventory.")
    
def delete():
    name = input("Enter the product name to delete: ")
    for product in products:
        if product['name'].lower() == name.lower():
            confirm = input(f"Are you sure you want to delete '{name}'? (yes/no): ").lower()
            if confirm == 'yes':
                products.remove(product)
                print(f"Product '{name}' deleted successfully.")
            else:
                print("Deletion cancelled.")
            return
    print(f"Product '{name}' not found in inventory.")
def generate():
    total = 0
    for product in products:
        total += float(product['price']) * int(product['quantity'])
    print(f"Total inventory value: ${total:.2f}")
```
    
