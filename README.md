import tkinter as tk
from tkinter import messagebox

# Función para añadir datos
def añadir_dato():
    texto = entrada_texto.get()
    if texto.strip():
        lista_datos.insert(tk.END, texto)
        entrada_texto.delete(0, tk.END)
    else:
        messagebox.showerror("Error", "Debe ingresar un valor antes de agregar.")

# Función para limpiar la lista
def borrar_lista():
    lista_datos.delete(0, tk.END)

# Función para salir de la aplicación
def salir():
    ventana.destroy()

# Ventana principal
ventana = tk.Tk()
ventana.title("Gestor de Datos - Tkinter")
ventana.geometry("420x380")
ventana.config(bg="#e6f2ff")

# Frame principal
marco = tk.Frame(ventana, bg="#cce0ff", bd=5, relief="ridge")
marco.pack(padx=20, pady=20, fill="both", expand=True)

# Título
titulo = tk.Label(marco, text="Aplicación GUI Básica", font=("Helvetica", 14, "bold"), bg="#cce0ff")
titulo.pack(pady=10)

# Entrada de texto
lbl = tk.Label(marco, text="Ingrese un dato:", bg="#cce0ff", font=("Arial", 10))
lbl.pack()
entrada_texto = tk.Entry(marco, width=35)
entrada_texto.pack(pady=5)

# Botones
btn_frame = tk.Frame(marco, bg="#cce0ff")
btn_frame.pack(pady=10)

btn_agregar = tk.Button(btn_frame, text="Agregar", command=añadir_dato, bg="#99ffcc", width=10)
btn_agregar.grid(row=0, column=0, padx=5)

btn_borrar = tk.Button(btn_frame, text="Limpiar", command=borrar_lista, bg="#ff9999", width=10)
btn_borrar.grid(row=0, column=1, padx=5)

btn_salir = tk.Button(btn_frame, text="Salir", command=salir, bg="#cccccc", width=10)
btn_salir.grid(row=0, column=2, padx=5)

# Lista de datos
lista_datos = tk.Listbox(marco, width=45, height=10)
lista_datos.pack(pady=10)

# Ejecutar app
ventana.mainloop()
