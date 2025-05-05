import tkinter as tk
import random
from PIL import Image, ImageTk

# List of surprise quotes
quotes = [
    "You are amazing just the way you are!",
    "Keep shining, the world needs your light!",
    "Smile! It's the best accessory you can wear!",
    "You're capable of incredible things!",
    "Stay positive, work hard, and make it happen!"
]

def show_random_quote(label):
    quote = random.choice(quotes)
    label.config(text=quote)

def create_greeting_window():
    window = tk.Tk()
    window.title("Surprise Greeting App")
    window.geometry("650x500")
    window.configure(bg="#FFF0F5")  # Light pink background

    # Greeting header
    header = tk.Label(
        window,
        text="Hello, Sunshine!",
        font=("Comic Sans MS", 34, "bold"),
        fg="#FF1493",
        bg="#FFF0F5"
    )
    header.pack(pady=20)

    # Load and display an image
    try:
        image = Image.open("smile.png")  # Replace with your image
        image = image.resize((180, 180), Image.ANTIALIAS)
        photo = ImageTk.PhotoImage(image)
        image_label = tk.Label(window, image=photo, bg="#FFF0F5")
        image_label.image = photo
        image_label.pack(pady=10)
    except Exception:
        error_label = tk.Label(window, text="Image not found.", fg="red", bg="#FFF0F5")
        error_label.pack()

    # Quote display
    quote_label = tk.Label(
        window,
        text="Click below for a surprise quote!",
        font=("Verdana", 14),
        fg="#8A2BE2",
        bg="#FFF0F5",
        wraplength=500,
        justify="center"
    )
    quote_label.pack(pady=15)

    # Button to change quotes
    quote_button = tk.Button(
        window,
        text="Surprise Me!",
        font=("Helvetica", 16, "bold"),
        fg="white",
        bg="#32CD32",
        command=lambda: show_random_quote(quote_label),
        padx=12,
        pady=6
    )
    quote_button.pack(pady=10)

    # Closing note
    footer = tk.Label(
        window,
        text="Wishing you a colorful, happy day!",
        font=("Georgia", 12),
        fg="#DC143C",
        bg="#FFF0F5"
    )
    footer.pack(pady=20)

    window.mainloop()

create_greeting_window()
