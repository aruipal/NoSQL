# Abrir MongoDB en CMD :desktop_computer:
- Nos aseguramos de que el servicio esté en ejecución:
  <pre><code>docker ps -a</code></pre>
  <pre><code>docker start mongodb_container</code></pre>
- Conectarse al contenedor:
  <pre><code>docker exec -it mongodb_container mongosh</code></pre>
- Autenticarse:
  <pre><code>use admin</code></pre>
  <pre><code>db.auth("admin","admin123")</code></pre>
- Seleccionamos o creamos la base de datos:
  <pre><code>use mi_base</code></pre>
<img src="https://github.com/aruipal/UNIX/" alt="shell" width="350" />

