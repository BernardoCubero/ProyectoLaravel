# 🎯 LaravelEventManager

**LaravelEventManager** es una aplicación de gestión de eventos desarrollada con Laravel. Permite a los usuarios crear, visualizar, editar y eliminar eventos dentro de un sistema centralizado. Este proyecto fue desarrollado con fines académicos, utilizando una versión antigua de Laravel (5.x), lo cual implicó una serie de desafíos técnicos durante su puesta en marcha.

## 🔧 Problemas encontrados con `php artisan` y cómo los resolvimos

Durante la instalación y ejecución del proyecto, nos encontramos con los siguientes problemas:

- ❌ **Error:** `Laravel requires the Mcrypt PHP extension.`  
  **Causa:** Laravel 5 depende de `mcrypt`, una extensión eliminada en PHP 7.2+.  
  **Solución:** Comentamos manualmente el chequeo en el archivo:
  ```
  vendor/laravel/framework/src/Illuminate/Encryption/EncryptionServiceProvider.php
  ```
  Además, cambiamos el cifrado en `config/app.php` de:
  ```php
  'cipher' => 'MCRYPT_RIJNDAEL_128',
  ```
  a:
  ```php
  'cipher' => 'AES-256-CBC',
  ```

- ❌ **Error:** `composer install` fallaba por dependencias incompatibles con PHP 7.4.  
  **Solución:** Borramos `composer.lock` y `vendor/` y luego ejecutamos:
  ```bash
  composer install --no-scripts
  ```

- ❌ **Error:** Laravel seguía lanzando el mensaje de `Mcrypt` tras modificar los archivos.  
  **Solución:** Verificamos que el mensaje estaba cacheado o duplicado y ejecutamos:
  ```bash
  grep -R "Laravel requires the Mcrypt PHP extension" .
  ```
  para encontrar todas las copias y comentarlas.

## 📊 Documentación UML

> Para complementar el desarrollo del proyecto, hemos creado:
- ✅ Diagrama de clases del sistema
- ✅ Diagrama de comportamiento (secuencia o actividad)
  
Estos diagramas reflejan la estructura de las entidades y el flujo lógico del sistema.

## 👨‍💻 Integrantes del Grupo

- Pablo Herrador
- Rafael Moreno
- Germán Gutiérrez
- Bernardo Cubero

## 🛠️ Tecnologías utilizadas

- PHP 7.4
- Laravel 5.x
- MySQL
- Composer
- HTML5 / Blade

## 🚀 Instalación

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu-usuario/LaravelEventManager.git
   ```

2. Accede al proyecto:
   ```bash
   cd LaravelEventManager
   ```

3. Instala las dependencias:
   ```bash
   composer install --no-scripts
   ```

4. Configura el archivo `.env`:
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

5. Inicia el servidor:
   ```bash
   php artisan serve
   ```

## 📌 Notas

> Este proyecto utiliza una versión antigua de Laravel. Se han realizado modificaciones para que sea compatible con PHP 7.4 eliminando la dependencia de `mcrypt`.

## 📷 Capturas de pantalla

*(Aquí puedes añadir imágenes o gifs del dashboard si lo deseas)*

## 📄 Licencia

Este proyecto es académico y no se encuentra bajo ninguna licencia comercial.

## Diagrama de clases simple
![DiagramaDeClases](https://github.com/user-attachments/assets/de0b45fc-21cf-4a72-9308-d12c53140135)

## Diagrama de secuencia
![image](https://github.com/user-attachments/assets/c234fafc-6845-42bd-8be0-94eb488808d7)
