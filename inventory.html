import sqlite3
from datetime import datetime

# Connect to database (creates file if it doesn't exist)
conn = sqlite3.connect("giftshop.db")
cursor = conn.cursor()

# --- Create Tables ---
cursor.execute('''
CREATE TABLE IF NOT EXISTS inventory (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    item_name TEXT,
    color TEXT,
    size TEXT,
    type TEXT,
    quantity INTEGER,
    price REAL,
    manufacture_date TEXT
)
''')

cursor.execute('''
CREATE TABLE IF NOT EXISTS sales (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    item_id INTEGER,
    quantity_sold INTEGER,
    total_price REAL,
    sale_date TEXT,
    FOREIGN KEY(item_id) REFERENCES inventory(id)
)
''')

conn.commit()

# --- Functions ---

def add_item(item_name, color, size, type_, quantity, price, mfg_date):
    cursor.execute('''
    INSERT INTO inventory (item_name, color, size, type, quantity, price, manufacture_date)
    VALUES (?, ?, ?, ?, ?, ?, ?)
    ''', (item_name, color, size, type_, quantity, price, mfg_date))
    conn.commit()
    print("Item added successfully.")

def view_inventory():
    print("\n--- Inventory ---")
    for row in cursor.execute("SELECT * FROM inventory"):
        print(row)

def sell_item(item_id, quantity_sold):
    cursor.execute("SELECT quantity, price FROM inventory WHERE id=?", (item_id,))
    result = cursor.fetchone()
    if result:
        current_quantity, price = result
        if current_quantity >= quantity_sold:
            total_price = price * quantity_sold
            cursor.execute("UPDATE inventory SET quantity=? WHERE id=?", (current_quantity - quantity_sold, item_id))
            cursor.execute('''
            INSERT INTO sales (item_id, quantity_sold, total_price, sale_date)
            VALUES (?, ?, ?, ?)
            ''', (item_id, quantity_sold, total_price, datetime.now().strftime("%Y-%m-%d %H:%M:%S")))
            conn.commit()
            print("Sale recorded successfully.")
        else:
            print("Not enough stock.")
    else:
        print("Item not found.")

def view_sales():
    print("\n--- Sales History ---")
    for row in cursor.execute('''
    SELECT sales.id, inventory.item_name, sales.quantity_sold, sales.total_price, sales.sale_date
    FROM sales
    JOIN inventory ON sales.item_id = inventory.id
    '''):
        print(row)

# --- CLI Example ---
if __name__ == "__main__":
    while True:
        print("\n1. Add Item")
        print("2. View Inventory")
        print("3. Sell Item")
        print("4. View Sales")
        print("5. Exit")
        choice = input("Choose an option: ")

        if choice == "1":
            name = input("Item Name: ")
            color = input("Color: ")
            size = input("Size: ")
            type_ = input("Type (e.g., mug, t-shirt): ")
            qty = int(input("Quantity: "))
            price = float(input("Price: "))
            mfg = input("Manufacture Date (YYYY-MM-DD): ")
            add_item(name, color, size, type_, qty, price, mfg)

        elif choice == "2":
            view_inventory()

        elif choice == "3":
            item_id = int(input("Enter Item ID: "))
            qty = int(input("Quantity to sell: "))
            sell_item(item_id, qty)

        elif choice == "4":
            view_sales()

        elif choice == "5":
            print("Exiting.")
            break

        else:
            print("Invalid option.")
