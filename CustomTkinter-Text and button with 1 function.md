##Generate window with text + button (size reactive)
#Author: yjspectro

import customtkinter as ctk

# Theme setup
ctk.set_appearance_mode("dark") #light or dark
ctk.set_default_color_theme("blue")

# Generate main window ("root window")
root = ctk.CTk()
root.geometry("400x200")
root.title("CustomTkinter example - button making")

#Save the initial state of the button
button_state = True

#Base font sizes
base_font_size = 18
base_font_size_button = 20

# Add label
label = ctk.CTkLabel(root, text="Hello, CustomTkinter!", font=("Times New Roman", base_font_size))
label.place(relx=0.5, rely=0.2, anchor="center")

# Add button
# Add button
def button_callback():
    global button_state

    if button_state:
        #Change the text of label
        label.configure(text="Die Schaltfläche ist angeklickt!")
        
        #Change the text and color of button
        button.configure(text="Abbrechen", font=("Arial", base_font_size_button), fg_color="#e8453c", hover_color="#b0221a")
    else:
        label.configure(text="Hallo, CustomTkinter!")
        button.configure(text="Klick!", font=("Arial", base_font_size_button), fg_color="#326abf",hover_color="#153896")

    button_state = not button_state #reverse the state of the button (True ↔ False

button = ctk.CTkButton(root, text="Klick!", font=("Arial", base_font_size_button), fg_color="#326abf",hover_color="#153896",command=button_callback)
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
