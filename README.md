# 🔐 Smart Password Manager (Tkinter Project)

## 📌 Project Description

The **Smart Password Manager** is a simple GUI-based application built using Python and Tkinter.
It allows users to securely store login credentials such as website names, usernames, and passwords in a structured text file.

This project also includes additional features like password generation, show/hide functionality, and clipboard copying, making it more interactive and useful.

---

## 🎯 Features

* 🖥️ User-friendly Tkinter GUI
* 🔒 Password hidden by default
* 👁️ Show/Hide password option
* 🎲 Random strong password generator
* 📋 Copy password to clipboard
* 💾 Save data in text file (table format)
* 📂 Custom file save location
* ⚠️ Alert messages using MessageBox

---

## 🛠️ Technologies Used

* Python 3.x
* Tkinter (built-in GUI library)
* Random module
* String module
* OS module

---

## 📂 File Storage Format

The stored file will look like this:

## WEBSITE             USERNAME            PASSWORD

gmail.com           user123             A@9kLm2!xQ
instagram           user_insta          7Hd@2kLmP!

---

## ▶️ How to Run

1. Install Python (3.x) on your system
2. Save the code as `password_manager.py`
3. Open terminal / command prompt
4. Run the program using:

```bash
python password_manager.py
```

---

## 🖼️ Output

* A GUI window will open
* User can enter details and save credentials
* Data will be stored in the selected file location

---

## 📚 Concepts Used

* Tkinter GUI design
* Event handling
* File handling (write & append modes)
* Random password generation
* Clipboard operations

---

## 🚀 Future Enhancements

* 🔐 Add master login password
* 🔍 Search saved passwords
* 🔒 Encrypt stored passwords
* 🎨 Improve UI design

---
##  Program
```
import tkinter as tk
from tkinter import messagebox, filedialog
import random
import string
import os

file_path = ""

# Choose file location
def choose_location():
    global file_path
    file_path = filedialog.asksaveasfilename(
        defaultextension=".txt",
        filetypes=[("Text Files", "*.txt")]
    )

    if file_path and not os.path.exists(file_path):
        with open(file_path, "w") as f:
            f.write(f"{'WEBSITE':<20}{'USERNAME':<20}{'PASSWORD':<20}\n")
            f.write("-" * 60 + "\n")

# Generate password
def generate_password():
    chars = string.ascii_letters + string.digits + "!@#$%"
    password = ''.join(random.choice(chars) for _ in range(10))
    entry_password.delete(0, tk.END)
    entry_password.insert(0, password)

# Copy password
def copy_password():
    root.clipboard_clear()
    root.clipboard_append(entry_password.get())
    messagebox.showinfo("Copied", "Password copied!")

# Show/Hide password
def toggle_password():
    if entry_password.cget('show') == "*":
        entry_password.config(show="")
    else:
        entry_password.config(show="*")

# Save data
def save_data():
    website = entry_website.get()
    username = entry_username.get()
    password = entry_password.get()

    if file_path == "":
        messagebox.showwarning("Warning", "Choose file location first!")
    elif website == "" or username == "" or password == "":
        messagebox.showwarning("Warning", "Fill all fields!")
    else:
        with open(file_path, "a") as f:
            f.write(f"{website:<20}{username:<20}{password:<20}\n")

        messagebox.showinfo("Success", "Saved Successfully!")

        entry_website.delete(0, tk.END)
        entry_username.delete(0, tk.END)
        entry_password.delete(0, tk.END)

# GUI
root = tk.Tk()
root.title("Smart Password Manager")
root.geometry("400x350")

tk.Label(root, text="Password Manager", font=("Arial", 16, "bold")).pack(pady=10)

tk.Label(root, text="Website").pack()
entry_website = tk.Entry(root)
entry_website.pack()

tk.Label(root, text="Username").pack()
entry_username = tk.Entry(root)
entry_username.pack()

tk.Label(root, text="Password").pack()
entry_password = tk.Entry(root, show="*")
entry_password.pack()

tk.Button(root, text="Generate Password", command=generate_password).pack(pady=5)
tk.Button(root, text="Show/Hide Password", command=toggle_password).pack(pady=5)
tk.Button(root, text="Copy Password", command=copy_password).pack(pady=5)

tk.Button(root, text="Choose Save Location", command=choose_location).pack(pady=5)
tk.Button(root, text="Save Data", command=save_data).pack(pady=5)

tk.Button(root, text="Exit", command=root.quit).pack(pady=5)

root.mainloop()
```
## Output
<img width="1426" height="1033" alt="image" src="https://github.com/user-attachments/assets/5412ac75-978a-411a-a8e8-e28290fe5366" />
<img width="897" height="830" alt="image" src="https://github.com/user-attachments/assets/4e8eb0f7-7811-4587-8f7f-abeea43e5d0f" />
<img width="516" height="526" alt="image" src="https://github.com/user-attachments/assets/2916437c-3421-4dd9-9433-15e0d90c3200" />


## ✅ Result

Thus, the **Smart Password Manager** project is successfully implemented using Python Tkinter and executed.

---

