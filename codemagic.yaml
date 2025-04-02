import sqlite3 from datetime import datetime

class Inventario: def init(self): self.conexion = sqlite3.connect("inventario.db") self.cursor = self.conexion.cursor() self.crear_tabla()

def crear_tabla(self):
    self.cursor.execute('''
        CREATE TABLE IF NOT EXISTS productos (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            nombre TEXT NOT NULL,
            codigo_barra TEXT UNIQUE,
            cantidad INTEGER NOT NULL,
            precio REAL NOT NULL,
            fecha_vencimiento TEXT,
            categoria TEXT NOT NULL,
            imagen TEXT,
            fecha_registro TEXT NOT NULL
        )
    ''')
    self.conexion.commit()

def agregar_producto(self, nombre, codigo_barra, cantidad, precio, categoria, imagen=None, fecha_vencimiento=None):
    fecha_registro = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    self.cursor.execute('''
        INSERT INTO productos (nombre, codigo_barra, cantidad, precio, categoria, imagen, fecha_vencimiento, fecha_registro)
        VALUES (?, ?, ?, ?, ?, ?, ?, ?)
    ''', (nombre, codigo_barra, cantidad, precio, categoria, imagen, fecha_vencimiento, fecha_registro))
    self.conexion.commit()

def mostrar_productos(self):
    self.cursor.execute("SELECT * FROM productos")
    return self.cursor.fetchall()

def mostrar_por_categoria(self, categoria):
    self.cursor.execute("SELECT * FROM productos WHERE categoria = ?", (categoria,))
    return self.cursor.fetchall()

def buscar_producto(self, codigo_barra):
    self.cursor.execute("SELECT * FROM productos WHERE codigo_barra = ?", (codigo_barra,))
    return self.cursor.fetchone()

def actualizar_producto(self, id_producto, cantidad, precio):
    self.cursor.execute("""
        UPDATE productos
        SET cantidad = ?, precio = ?
        WHERE id = ?
    """, (cantidad, precio, id_producto))
    self.conexion.commit()

def eliminar_producto(self, id_producto):
    self.cursor.execute("DELETE FROM productos WHERE id = ?", (id_producto,))
    self.conexion.commit()

def cerrar_conexion(self):
    self.conexion.close()

Ejemplo de uso

tiendadb = Inventario() tiendadb.agregar_producto("Leche", "123456789", 10, 1.5, "Líquidos", "leche.png", "2025-12-31") tiendadb.agregar_producto("Pan", "987654321", 20, 0.8, "Comestibles", "pan.png") print("Todos los productos:", tiendadb.mostrar_productos()) print("Productos líquidos:", tiendadb.mostrar_por_categoria("Líquidos")) tiendadb.cerrar_conexion()



