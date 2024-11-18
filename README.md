# Seguridad en el arranque de tu Linux
Guía práctica para fortalecer la seguridad en sistemas Linux. Aprende a mitigar el acceso no autorizado a través del modo recovery.
### 1. Genera una contraseña para GRUB: ###
  ```
  grub-mkpasswd-pbkdf2
  ```
Obtendrás algo como esto:
  PBKDF2 hash of your password is grub.pbkdf2.sha512.10000.<cadena encriptada>

### 2. Configura la contraseña en GRUB: ###
Edita el archivo de configuración de GRUB personalizado:
  ```
  sudo nano /etc/grub.d/40_custom
  ```
Agrega las siguientes líneas al archivo:
  ```
  set superusers="root"
  password_pbkdf2 root grub.pbkdf2.sha512.10000.<cadena encriptada>
  ```

### 3. Aplica la configuración: ###
Guarda el archivo (Ctrl+O y Ctrl+X en nano) y luego ejecuta:
  ```
  sudo update-grub
  ```

A partir de ahora GRUB te pedirá la contraseña configurada antes de permitirte:
  - Editar las entradas del menú GRUB.
  - Acceder al modo recovery.
  - Ejecutar comandos desde la consola GRUB.

