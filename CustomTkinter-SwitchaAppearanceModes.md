# Change the Appearance Mode by True ↔ False
## 1. Use clicking button
```
import customtkinter as ctk

# Theme setup
ctk.set_appearance_mode("light") #light or dark
ctk.set_default_color_theme("blue")

# Generate main window ("root window")
root = ctk.CTk()
root.geometry("400x200")
root.title("CustomTkinter example - Appearance mode toggle")

#Save the initial state of the button
button_state = True

#Base font sizes
base_font_size = 18
base_font_size_button = 20

#Add label
label = ctk.CTkLabel(root, text="Change the appearance mode", font=("Times New Roman", base_font_size))
label.place(relx=0.5, rely=0.2, anchor="center")

# Add button
def button_callback():
    global button_state

    if button_state:
        ctk.set_appearance_mode("dark")
        button.configure(text="Lichtmodus", font=("Arial", base_font_size_button))
    else:
        ctk.set_appearance_mode("light")
        button.configure(text="Dunkelmodus", font=("Arial", base_font_size_button))

    button_state = not button_state #reverse the state of the button (True ↔ False)

button = ctk.CTkButton(root, text="Dunkelmodus", font=("Arial", base_font_size_button),command=button_callback)
button.place(relwidth=0.5, relheight=0.2,relx=0.5, rely=0.6, anchor="center") #relative size of the button

#Resize font function (adjusts both label & button text)
def resize_font(event):
    new_size = int(root.winfo_width() * 0.05) #reltaive size of the text
    new_size = max(10, new_size) #lower limit of the text
    label.configure(font=("Times New Roman", new_size))

    new_size_button = int(root.winfo_width() * 0.06) 
    new_size_button = max(12, new_size_button)
    button.configure(font=("Arial", new_size_button))


#Bind window resizing event
root.bind("<Configure>",resize_font)

# Run
root.mainloop()
```
---
## 2. Use toggle
```
import customtkinter as ctk

# Theme setup
ctk.set_appearance_mode("light") #light or dark
ctk.set_default_color_theme("blue")

# Generate main window ("root window")
root = ctk.CTk()
root.geometry("400x200")
root.title("CustomTkinter example - Appearance mode toggle")

#Base font sizes
base_font_size = 18
base_font_size_switch = 16

#Add label
label = ctk.CTkLabel(root, text="Change the appearance mode", font=("Times New Roman", base_font_size))
label.place(relx=0.5, rely=0.2, anchor="center")

# Add button
def toggle_callback():
    if mode_switch.get()==1:
        ctk.set_appearance_mode("dark")
        mode_switch.configure(text="  Lichtmodus")
    else:
        ctk.set_appearance_mode("light")
        mode_switch.configure(text="  Dunkelmodus")

mode_switch = ctk.CTkSwitch(root, text="  Dunkelmodus", font=("Arial", base_font_size_switch), command=toggle_callback)
mode_switch.place(relwidth=0.5, relheight=0.2,relx=0.55, rely=0.6, anchor="center") #relative size of the button

#Resize font function (adjusts both label & button text)
def resize_font(event):
    new_size = int(root.winfo_width() * 0.05) #reltaive size of the text
    new_size = max(10, new_size) #lower limit of the text
    label.configure(font=("Times New Roman", new_size))

    new_size_mode_switch = int(root.winfo_width() * 0.04) 
    new_size_mode_switch = max(10, new_size_mode_switch)
    mode_switch.configure(font=("Arial", new_size_mode_switch))


#Bind window resizing event
root.bind("<Configure>",resize_font)

# Run
root.mainloop()
```
