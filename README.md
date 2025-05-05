Laboratorio 3
Desafíos semanales 3
Operaciones CRUD con ADO.NET
Aprender a manipular datos desde C# (insertar, modificar, eliminar y consultar)


Usar comandos SQL desde la aplicación


Practicar el uso de SqlCommand y parámetros


Subir avances al repositorio de GitHub



¿Qué es CRUD?
C: Create (Insertar)


R: Read (Leer o consultar)


U: Update (Modificar)


D: Delete (Eliminar)


¿Por qué usar parámetros en SQL?
Para evitar inyecciones de código malicioso


Para que los valores se pasen de forma segura


Para reutilizar consultas



🛠️ Preparar el proyecto
Usaremos el mismo proyecto de la Semana 2 (hay que clonar el repositorio

🔹 Agregar un producto (CREATE)
string insertQuery = "INSERT INTO Productos (Nombre, Descripcion, Precio, Stock, CategoriaId) VALUES (@nombre, @descripcion, @precio, @stock, @categoriaId)";
SqlCommand cmd = new SqlCommand(insertQuery, conn);
cmd.Parameters.AddWithValue("@nombre", "Mouse inalámbrico");
cmd.Parameters.AddWithValue("@descripcion", "Mouse óptico USB");
cmd.Parameters.AddWithValue("@precio", 150000);
cmd.Parameters.AddWithValue("@stock", 20);
cmd.Parameters.AddWithValue("@categoriaId", 1); // Tecnología
cmd.ExecuteNonQuery();
Console.WriteLine("✅ Producto agregado con éxito.");

🔹 Consultar productos (READ)
string selectQuery = "SELECT P.Nombre, P.Precio, P.Stock, C.Nombre AS Categoria FROM Productos P JOIN Categorias C ON P.CategoriaId = C.Id";
SqlCommand cmd = new SqlCommand(selectQuery, conn);
SqlDataReader reader = cmd.ExecuteReader();
while (reader.Read())
{
    Console.WriteLine($"{reader["Nombre"]} - ${reader["Precio"]} - Stock: {reader["Stock"]} - Categoría: {reader["Categoria"]}");
}
reader.Close();


🔹 Modificar un producto (UPDATE)
string updateQuery = "UPDATE Productos SET Precio = @precio WHERE Nombre = @nombre";
SqlCommand cmd = new SqlCommand(updateQuery, conn);
cmd.Parameters.AddWithValue("@precio", 175000);
cmd.Parameters.AddWithValue("@nombre", "Mouse inalámbrico");
cmd.ExecuteNonQuery();
Console.WriteLine("🔄 Producto actualizado.");

🔹 Eliminar un producto (DELETE)
string deleteQuery = "DELETE FROM Productos WHERE Nombre = @nombre";
SqlCommand cmd = new SqlCommand(deleteQuery, conn);
cmd.Parameters.AddWithValue("@nombre", "Mouse inalámbrico");
cmd.ExecuteNonQuery();
Console.WriteLine("❌ Producto eliminado.");


🎯 Ejercicio CRUD
Pedir al usuario que elija una opción:
 1-Agregar / 2-Listar / 3-Modificar precio / 4-Eliminar


Ejecutar la acción según la opción usando SqlCommand


Mostrar resultados por consola


Guardar y subir los cambios a GitHub

Subir a GitHub
Crear una rama de GIT

Guardar los cambios


Hacer commit: "Implementación de operaciones CRUD"


Hacer push al repositorio remoto


Verificar en GitHub

Ejercicios finales
✅ Ampliar el CRUD para permitir elegir el producto por su código

✅ Permitir modificar también la descripción del producto

✅ Subir a GitHub

![Captura de pantalla 2025-05-04 195516](https://github.com/user-attachments/assets/7d08ecea-cf23-4ce3-9387-15ec04a2f7a6)


![Captura de pantalla 2025-05-04 195755](https://github.com/user-attachments/assets/51911aa6-2e36-4ef1-a525-d22c29113e98)


![Captura de pantalla 2025-05-04 195811](https://github.com/user-attachments/assets/912149ed-d6a9-4977-9b0c-1b195b52d770)


![Captura de pantalla 2025-05-04 195859](https://github.com/user-attachments/assets/61805bff-95b9-48aa-8725-950e66df7d40)
