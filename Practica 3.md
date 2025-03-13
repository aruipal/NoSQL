# MODELADO DE DATOS EN MONGODB :blush:
### 1. Creación de una base de datos y colección:
<pre><code id="codigo">use tienda</code></pre>
<pre><code id="codigo">db.clientes.insertMany([{nombre: "Carlos Pérez", email: "carlos@example.com", pedidos: [{producto: "Laptop", cantidad: 1, precio: 1200}, {producto: "Ratón", cantidad: 2, precio: 25}]},{nombre: "Ana López", email: "ana@example.com", pedidos: [{producto: "Teclado", cantidad: 1, precio: 50}]}])</code></pre>
### 2. Consultar datos en documentos anidados:
<pre><code id="codigo">db.clientes.find().pretty()</code></pre>
 - <b>Buscar un cliente específico:</b>
   <pre><code id="codigo">db.clientes.find({ nombre: "Carlos Pérez" }).pretty()</code></pre>
- <b>Buscar pedidos con un producto específico:</b>
  <pre><code id="codigo">db.clientes.find({ "pedidos.producto": "Laptop" }).pretty()</code></pre>
### 3. Actualizar datos en documentos anidados:
- <b>Modificar un campo dentro de un documento anidado:</b>
 Supongamos que queremos actualizar el precio del Ratón en los pedidos de Carlos Pérez:
 <pre><code id="codigo">db.clientes.updateOne({nombre: "Carlos Pérez", "pedidos.producto": "Ratón"}, { $set: { "pedidos.$.precio": 30 }})</code></pre>
 - <b>Añadir un nuevo pedido al cliente</b>
  Si Ana López compra un monitor, podemos agregarlo a su lista de pedidos:
 <pre><code id="codigo">db.clientes.updateOne( { nombre: "Ana López" },{ $push: { pedidos: {producto: "Monitor", cantidad: 1, precio: 200 } } } )</code></pre>
### 4. Eliminar datos en documentos anidados:
- <b>Eliminar un pedido específico:</b>
 Si Carlos Pérez decide cancelar su compra del Ratón:
 <pre><code id="codigo">db.clientes.updateOne( { nombre: "Carlos Pérez"},{ $pull: { pedidos: { producto: "Ratón" } } } )</code></pre>
 - <b>Eliminar todos los pedidos de un cliente:</b>
  Si queremos dejar en blanco los pedidos de Ana López:
 <pre><code id="codigo">db.clientes.updateOne({ nombre: "Ana López" }, { $set: {pedidos: [] } } )</code></pre>
 - <b>Eliminar un cliente por completo:</b>
  Si un cliente ya no es necesario en la base de datos:
 <pre><code id="codigo">db.clientes.deleteOne({ nombre: "Carlos Pérez" })</code></pre>
### 5. Conclusión:
- <b>El modelado</b> anidado permite almacenar datos relacionados dentro de un
mismo documento, lo que mejora la velocidad de lectura y la organización de
datos estrechamente relacionados. Sin embargo, puede generar documentos
muy grandes y difíciles de actualizar si los datos cambian con frecuencia.
- Por otro lado, <b>el modelado de referencias</b> separa los datos en diferentes
colecciones y los une mediante identificadores, reduciendo la redundancia y
facilitando las actualizaciones. No obstante, requiere consultas adicionales para
recuperar la información.
<pre><code id="codigo">db.autores.insertMany([ { _id: ObjectId("6601a1b2c3d4e5f678901234"), nombre: "Gabriel García Márquez", nacionalidad: "Colombiano" }, { _id: ObjectId("6601a1b2c3d4e5f678912345"), nombre: "J.K. Rowling", nacionalidad: "Británica" } ] )</code></pre>
<pre><code id="codigo">db.libos.insertMany([ { titulo: "Cien años de soledad", año: 1967, autor_id:ObjectId("6601a1b2c3d4e5f678901234") }, { titulo: "Harry Potter y la piedra filosofal", año: 1997, autor_id: ObjectId("6601a1b2c3d4e5f678912345")}]) </code></pre>







