# MODELADO DE DATOS EN MONGODB
### 1. Creación de una base de datos y colección:
<pre><code id="codigo">use tienda</code></pre>
<pre><code id="codigo">db.clientes.insertMany([{nombre: "Carlos Pérez", email: "carlos@example.com", pedidos: [{producto: "Laptop", cantidad: 1, precio: 1200}, {producto: "Ratón", cantidad: 2, precio: 25}]},{nombre: "Ana López", email: "ana@example.com", pedidos: [{producto: "Teclado", cantidad: 1, precio: 50}]}])</code></pre>
