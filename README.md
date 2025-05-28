# Sistema de Inicio de Sesión y Registro de Usuarios en ASP.NET MVC 5

Este proyecto demuestra cómo implementar un **formulario de inicio de sesión y registro de usuarios** en **ASP.NET MVC 5** utilizando **C# y SQL Server**, con enfoque en **validación de usuario**, **encriptación de contraseña (SHA256)**, **procedimientos almacenados**, y **manejo de sesiones**.

> ✅ Proyecto desarrollado con **Visual Studio 2022**

---

## 🎯 Funcionalidades Principales

- Formulario de inicio de sesión y registro de usuarios
- Validación segura de credenciales
- Encriptación de contraseñas (SHA256)
- Uso de procedimientos almacenados (SQL Server)
- Manejo de sesiones
- Redirección a página principal tras autenticación

---

## 🔐 Flujo de Autenticación

### 1. Formulario de Inicio de Sesión
El usuario ingresa su nombre de usuario y contraseña.

### 2. Envío al Controlador
Los datos se reciben en `AccesoController`, donde se realiza la validación.

### 3. Consulta a Base de Datos
Se utiliza el procedimiento almacenado `sp_ValidarUsuario` para validar la existencia del usuario.

### 4. Verificación de Contraseña
La contraseña ingresada se transforma usando SHA256 y se compara con la contraseña almacenada.

### 5. Sesión y Redirección
Si la validación es exitosa, se inicia sesión y se redirige al usuario a la página principal (`HomeController`).

---

## 🧠 Consideraciones de Seguridad

- Las contraseñas se almacenan **encriptadas con SHA256**.
- Se evita almacenar datos sensibles en texto plano.
- Se valida la entrada del usuario para prevenir **inyección SQL**.

Para generar el hash SHA256 se puede utilizar:  
🔗 https://emn178.github.io/online-tools/sha256.html

---

## ⚙️ Stack Tecnológico

- **ASP.NET MVC 5**
- **C#**
- **SQL Server**
- **Stored Procedures**
  sp_RegistrarUsuario, sp_ValidarUsuario
- **Sessions**
- **Bootstrap (UI)**

---

## 📁 Estructura del Proyecto

Proyecto/

│

├── Content/ → Estilos CSS (Bootstrap)

├── Controllers/

│ ├── AccesoController.cs → Lógica de autenticación

│ └── HomeController.cs → Página principal

│
├── Models/

│ └── Usuario.cs → Modelo del usuario
│
├── Permisos/

│ └── ValidarSesionAttribute.cs → Validación de sesión

│
├── Scripts/ → Archivos JS (Bootstrap)

│
├── Views/

│ ├── Acceso/

│ │ ├── Login.cshtml → Formulario de inicio de sesión

│ │ └── Registrar.cshtml → Formulario de registro

│ └── Home/

│ │ ├── About.cshtml → Página de prueba

│ │ └── Contact.cshtml → Página de prueba

│ │ └── Index.cshtml → Página principal

│
└── DB_ACCESO.sql → Script SQL (tabla y procedimientos)



## 🧾 Script de Base de Datos: `DB_ACCESO.sql`

Contiene:

- **Tabla:** `USUARIO`
- **Procedimientos almacenados:**
  - `sp_RegistrarUsuario`
  - `sp_ValidarUsuario`

```sql
SELECT * FROM USUARIO
Ejemplo de inserción en SQL Server

declare @registrado bit, @mensaje varchar(100)
exec sp_RegistrarUsuario 'jose@gmail.com','ecd71870d1963316a97e3ac3408c9835ad8cf0f3c1bc703527c30265534f75ae', @registrado output, @mensaje output
select @registrado
select @mensaje

🚀 Requisitos para Ejecutar
Visual Studio 2022
SQL Server

Configurar cadena de conexión en AccesoController.cs:

static string cadena = "Data Source=TU_SERVIDOR;Initial Catalog=DB_ACCESO;Integrated Security=True";

📩 Contacto
**Nombre: Maicolm Rivera Zamudio**

**Correo: grupoxpertos@gmail.com**

**LinkedIn: www.linkedin.com/in/maicolm-rivera-9537b6ba**

Este proyecto se ha diseñado con fines puramente demostrativos, formando parte de una evaluación técnica y como un ejemplo de la formación continua. El objetivo principal es mostrar las habilidades y capacidades adquiridas, así como demostrar la aplicación de los conocimientos en un contexto práctico. 
