# 🚗 Sistema de Arriendo de Autos - Laravel

[![Laravel](https://img.shields.io/badge/Laravel-10.x-red.svg)](https://laravel.com)
[![PHP](https://img.shields.io/badge/PHP-8.1+-blue.svg)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-8.0+-orange.svg)](https://mysql.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Descripción del Proyecto

Sistema de gestión de arriendo de vehículos desarrollado en Laravel que permite a los administradores gestionar vehículos, categorías y arriendos de manera eficiente. El sistema incluye autenticación de usuarios, validación de disponibilidad de vehículos y un dashboard administrativo completo.

## 🛠️ Stack Tecnológico

### Backend
- **Laravel 10.x** - Framework PHP
- **PHP 8.1+** - Lenguaje de programación
- **MySQL 8.0+** - Base de datos
- **Laravel Sanctum** - Autenticación API

### Frontend
- **Blade Templates** - Motor de plantillas
- **Bootstrap 5** - Framework CSS
- **jQuery** - Biblioteca JavaScript
- **DataTables** - Tablas interactivas
- **Vite** - Build tool para assets

### Herramientas de Desarrollo
- **Composer** - Gestor de dependencias PHP
- **PHPUnit** - Framework de testing
- **Laravel Pint** - Code style fixer
- **Faker** - Generador de datos de prueba

## 🚀 Funcionalidades Principales

### 👤 Gestión de Usuarios
- Sistema de autenticación completo
- Registro e inicio de sesión
- Middleware de autenticación para rutas protegidas

### 🚙 Gestión de Vehículos
- **CRUD completo** de vehículos
- Categorización por tipo (Sedán, SUV, Pickup, Hatchback, Sports Car)
- Validación de patentes únicas
- Información detallada: marca, modelo, año, patente

### 📋 Gestión de Categorías
- Creación y administración de categorías de vehículos
- Relación uno a muchos con vehículos
- Seeders predefinidos para categorías comunes

### 🏢 Gestión de Arriendos
- **Registro de clientes** con validación completa
- **Validación de disponibilidad** de vehículos por fechas
- Gestión de fechas de entrega y devolución
- Soft deletes para preservar historial
- Exportación a Excel y PDF

### 📊 Dashboard Administrativo
- Vista general de arriendos activos
- Estadísticas por categoría
- Tablas interactivas con DataTables
- Contador de arriendos totales

## 🗄️ Estructura de Base de Datos

### Tablas Principales

#### `users`
- `id`, `name`, `email`, `password`, `timestamps`

#### `categories`
- `id`, `name`, `timestamps`

#### `vehicles`
- `id`, `category_id`, `patent`, `year`, `brand`, `model`, `timestamps`
- **Relación**: `belongsTo` Category

#### `clientes` (Arriendos)
- `id`, `vehicle_id`, `names`, `lastname`, `lastname2`, `RUT`, `email`, `deadline`, `returndate`, `deleted_at`, `timestamps`
- **Relación**: `belongsTo` Vehicle
- **Soft Deletes** habilitado

## 📦 Instalación y Configuración

### Prerrequisitos
- PHP 8.1 o superior
- Composer
- MySQL 8.0 o superior
- XAMPP (recomendado para desarrollo local)

### Pasos de Instalación

1. **Clonar el repositorio**
```bash
git clone <repository-url>
cd ArriendoAutos-Laravel
```

2. **Instalar dependencias**
```bash
composer install
npm install
```

3. **Configurar variables de entorno**
```bash
cp .env.example .env
php artisan key:generate
```

4. **Configurar base de datos**
Editar el archivo `.env`:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=arriendo_autos
DB_USERNAME=root
DB_PASSWORD=
```

5. **Ejecutar migraciones y seeders**
```bash
php artisan migrate
php artisan db:seed
```

6. **Compilar assets**
```bash
npm run dev
# o para producción
npm run build
```

7. **Iniciar servidor**
```bash
php artisan serve
```

El sistema estará disponible en `http://localhost:8000`

## 🎯 Uso del Sistema

### Acceso al Sistema
1. Navegar a `http://localhost:8000/login`
2. Registrarse como nuevo usuario o iniciar sesión
3. Acceder al dashboard administrativo

### Gestión de Vehículos
- **Agregar vehículo**: Seleccionar categoría, ingresar patente, año, marca y modelo
- **Eliminar vehículo**: Botón de eliminación en la lista de vehículos

### Gestión de Arriendos
- **Nuevo arriendo**: Acceder a "Nuevo Arriendo"
- **Datos requeridos**: Información del cliente, vehículo y fechas
- **Validación automática**: El sistema verifica disponibilidad del vehículo
- **Finalizar arriendo**: Botón "Entregado" para marcar como completado

### Exportación de Datos
- **Excel**: Exportar lista de arriendos a formato Excel
- **PDF**: Generar reporte en PDF de arriendos activos

## 🧪 Testing

El proyecto incluye configuración básica de PHPUnit:

```bash
# Ejecutar todos los tests
php artisan test

# Ejecutar tests específicos
php artisan test --filter=ExampleTest
```

### Estructura de Tests
- `tests/Feature/` - Tests de funcionalidad
- `tests/Unit/` - Tests unitarios
- Configuración en `phpunit.xml`

## 📁 Estructura del Proyecto

```
ArriendoAutos-Laravel/
├── app/
│   ├── Http/Controllers/     # Controladores
│   ├── Models/              # Modelos Eloquent
│   └── Providers/           # Service Providers
├── database/
│   ├── migrations/          # Migraciones de BD
│   └── seeders/            # Seeders de datos
├── resources/
│   ├── views/              # Vistas Blade
│   ├── css/               # Estilos CSS
│   └── js/                # JavaScript
├── routes/
│   └── web.php            # Rutas web
├── public/                # Archivos públicos
└── tests/                 # Tests automatizados
```

## 🔧 Configuración Adicional

### XAMPP Setup (Windows)
1. Instalar XAMPP desde [apachefriends.org](https://www.apachefriends.org)
2. Verificar configuración de `php.ini`
3. Iniciar servicios Apache y MySQL
4. Crear base de datos `arriendo_autos` en phpMyAdmin

### Composer Setup
1. Descargar Composer desde [getcomposer.org](https://getcomposer.org)
2. Instalar siguiendo las instrucciones del instalador
3. Verificar instalación: `composer --version`

## 🚀 Mejoras Sugeridas

### Funcionalidades Futuras
- [ ] **Sistema de pagos** integrado
- [ ] **Notificaciones por email** para recordatorios
- [ ] **API REST** para aplicación móvil
- [ ] **Sistema de calificaciones** de vehículos
- [ ] **Reportes avanzados** con gráficos
- [ ] **Gestión de mantenimiento** de vehículos
- [ ] **Sistema de multas** por retrasos
- [ ] **Integración con GPS** para tracking

### Mejoras Técnicas
- [ ] **Implementar tests completos** (Feature y Unit)
- [ ] **Agregar validación de RUT chileno**
- [ ] **Implementar cache** para consultas frecuentes
- [ ] **Agregar logs de auditoría**
- [ ] **Implementar rate limiting**
- [ ] **Agregar documentación API** (Swagger)
- [ ] **Optimizar consultas** con eager loading
- [ ] **Implementar queue jobs** para tareas pesadas

### Mejoras de UX/UI
- [ ] **Diseño responsive** mejorado
- [ ] **Tema oscuro/claro**
- [ ] **Búsqueda avanzada** de vehículos
- [ ] **Filtros por categoría** y disponibilidad
- [ ] **Calendario visual** para disponibilidad
- [ ] **Dashboard con métricas** en tiempo real

## 🤝 Contribución

1. Fork el proyecto
2. Crear una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abrir un Pull Request

## 📝 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo [LICENSE](LICENSE) para más detalles.

## 👥 Autores

- **Alonso Cuevas** - Desarrollo y documentación
- **Jeremy Ormeño** - Desarrollo y testing

## 📞 Soporte

Para soporte técnico o consultas sobre el proyecto, contactar a los desarrolladores o crear un issue en el repositorio.

---

⭐ **¡Si este proyecto te fue útil, no olvides darle una estrella!** ⭐
---
<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

You may also try the [Laravel Bootcamp](https://bootcamp.laravel.com), where you will be guided through building a modern Laravel application from scratch.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 2000 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the Laravel [Patreon page](https://patreon.com/taylorotwell).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Cubet Techno Labs](https://cubettech.com)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[Many](https://www.many.co.uk)**
- **[Webdock, Fast VPS Hosting](https://www.webdock.io/en)**
- **[DevSquad](https://devsquad.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[OP.GG](https://op.gg)**
- **[WebReinvent](https://webreinvent.com/?utm_source=laravel&utm_medium=github&utm_campaign=patreon-sponsors)**
- **[Lendio](https://lendio.com)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
