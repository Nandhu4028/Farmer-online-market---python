market = []  

def add_product():
    print("\n--- Add Product (Farmer) ---")
    name = input("Enter product name: ")
    price = float(input("Enter price: "))
    quantity = int(input("Enter quantity: "))
    
    product = {
        "name": name,
        "price": price,
        "quantity": quantity
    }
    market.append(product)
    print("Product added successfully!")

def view_products():
    print("\n--- Available Products ---")
    if not market:
        print("No products available yet.")
        return

    for i, product in enumerate(market):
        print(f"{i+1}. {product['name']} - ${product['price']} (Qty: {product['quantity']})")

def buy_product():
    view_products()
    if not market:
        return
    
    choice = int(input("Enter product number to buy: ")) - 1
    
    if choice < 0 or choice >= len(market):
        print("Invalid choice.")
        return
    
    amount = int(input("Enter quantity to buy: "))
    
    if amount > market[choice]["quantity"]:
        print("Not enough quantity available.")
        return
    
    market[choice]["quantity"] -= amount
    total = amount * market[choice]["price"]
    print(f"Purchase successful! Total cost: ${total}")

def main():
    while True:
        print("\n===== Farmers Online Market =====")
        print("1. Add Product (Farmer)")
        print("2. View Products")
        print("3. Buy Product")
        print("4. Exit")
        
        choice = input("Enter your choice: ")

        if choice == "1":
            add_product()
        elif choice == "2":
            view_products()
        elif choice == "3":
            buy_product()
        elif choice == "4":
            print("Thank you for using Farmers Online Market!")
            break
        else:
            print("Invalid option. Try again.")

if __name__ == "__main__":
    main()
