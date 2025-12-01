# Sistema de Inventario para Papelería EDUVAL

Sistema web desarrollado para la gestión de inventario de una papelería. Permite el control de productos, categorías, entradas, salidas y usuarios con diferentes niveles de acceso.

## Tecnologías utilizadas

- Python 3.8+
- Flask 3.0.0
- SQLAlchemy (ORM)
- SQLite (Base de datos)
- HTML5, CSS3, JavaScript
- Werkzeug (Seguridad y hash de contraseñas)

## Requisitos del sistema

- Python 3.8 o superior
- pip (gestor de paquetes de Python)
- Navegador web moderno (Chrome, Firefox, Edge)

## Instalación

### 1. Descomprimir el proyecto

Extraer el archivo ZIP en la ubicación deseada.

### 2. Crear entorno virtual (opcional pero recomendado)
```bash
python -m venv venv
```

### 3. Activar el entorno virtual

En Windows:
```bash
venv\Scripts\activate
```

En Linux/Mac:
```bash
source venv/bin/activate
```

### 4. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 5. Inicializar la base de datos

La base de datos se crea automáticamente al ejecutar la aplicación por primera vez. 

Para crear las categorías iniciales, ejecutar:
```bash
python crear_categorias.py
```

## Ejecución del proyecto
```bash
python app.py
```

El sistema estará disponible en: http://127.0.0.1:5000

## Configuración inicial

### Clave de registro de usuarios
Para registrar nuevos usuarios en el sistema se requiere la siguiente clave:
```
EDUVAL2025
```

### Primer usuario
Es necesario crear el primer usuario con rol de administrador desde la página de registro.

## Estructura del proyecto
```
EDUVAL/
├── app.py                          Aplicación principal de Flask
├── models.py                       Modelos de base de datos
├── crear_categorias.py             Script para crear categorías
├── requirements.txt                Dependencias del proyecto
├── database_schema.sql             Esquema de la base de datos
├── instance/
│   └── EDUVAL.db                  Base de datos SQLite
├── static/
│   └── css/
│       └── style.css              Estilos del sistema
└── templates/                      Plantillas HTML
    ├── base.html
    ├── index.html
    ├── login.html
    ├── registro.html
    ├── dashboard.html
    ├── productos.html
    ├── categorias.html
    ├── catalogo.html
    └── ...
```

## Funcionalidades del sistema

### Catálogo público
- Visualización de productos disponibles sin necesidad de iniciar sesión
- Integración con WhatsApp para realizar pedidos
- Información de stock en tiempo real

### Gestión de productos
- Agregar, editar y eliminar productos
- Control de stock actual y stock mínimo
- Organización por categorías
- Alertas de stock bajo

### Control de inventario
- Registro de entradas de mercancía
- Registro de salidas/ventas
- Historial de movimientos por producto
- Asociación de movimientos con usuarios

### Gestión de categorías
- Crear y editar categorías de productos
- Eliminación controlada (solo si no tienen productos asociados)

### Sistema de usuarios
- Registro de usuarios con clave de acceso
- Tres niveles de rol: Administrador, Empleado, Cajero
- Recuperación de contraseña por correo electrónico

### Dashboard administrativo
- Estadísticas generales del sistema
- Total de productos, categorías y usuarios
- Lista de productos con stock crítico
- Accesos rápidos a funciones principales

## Permisos por rol

El sistema cuenta con tres tipos de usuarios con diferentes niveles de acceso:

Administrador
- Acceso completo al sistema
- Puede agregar, editar y eliminar productos
- Gestiona categorías del inventario
- Registra entradas y salidas de mercancía
- Acceso al dashboard con estadísticas
- Administra usuarios del sistema

Empleado
- Visualiza todos los productos
- Registra únicamente entradas de mercancía
- No puede modificar productos ni categorías
- Acceso al catálogo público

Cajero
- Visualiza todos los productos
- Registra únicamente salidas de mercancía
- No puede modificar productos ni categorías
- Acceso al catálogo público

Todos los roles pueden acceder al catálogo público para consultar productos disponibles.


## Configuración de correo para recuperación de contraseñas

Para habilitar la recuperación de contraseñas por correo, es necesario configurar las credenciales SMTP de Gmail en app.py:
```python
app.config['MAIL_USERNAME'] = 'tu_correo@gmail.com'
app.config['MAIL_PASSWORD'] = 'tu_contraseña_de_aplicacion'
```

Nota: Se requiere crear una contraseña de aplicación desde la configuración de seguridad de Google.

## Notas adicionales

- La base de datos se crea automáticamente en la carpeta instance/
- Para uso en producción se recomienda cambiar app.secret_key y EMPLOYEE_REGISTER_KEY
- El sistema utiliza SQLite, adecuado para pequeñas y medianas empresas
- Los datos de ejemplo pueden crearse ejecutando crear_categorias.py

## Base de datos

El archivo database_schema.sql contiene el esquema completo de la base de datos con las siguientes tablas:

- usuarios: Información de usuarios del sistema
- categorias: Categorías de productos
- productos: Inventario de productos
- entradas: Registro de entradas de mercancía
- salidas: Registro de salidas/ventas
- password_reset_tokens: Tokens para recuperación de contraseñas

## Autor

Proyecto desarrollado como sistema de gestión de inventario para Papelería EDUVAL.
