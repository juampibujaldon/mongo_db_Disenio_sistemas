
# 🍃 Configuración de MongoDB con Docker

Este directorio contiene toda la configuración necesaria para levantar un servicio de MongoDB usando Docker y Docker Compose. Está diseñado para ser el backend de almacenamiento para el proyecto de Monitoreo de Servidores.

El servicio se inicializa automáticamente con usuarios y bases de datos predefinidas para los entornos de desarrollo y testing.



---
## 📁 Componentes

* **`docker-compose.yml`** (en la raíz del proyecto): El archivo principal que orquesta todos los servicios. La sección `mongodb` define cómo se construye y configura este contenedor.
* **`mongo/mongo-init/init.js`**: Un script que se ejecuta **una sola vez** cuando la base de datos se crea por primera vez. Su trabajo es crear los usuarios y las bases de datos (`DEV_MONITOREAR`, etc.) que la aplicación necesita.
* **`.env`** (en la raíz del proyecto): Archivo que contiene las **credenciales y contraseñas**. **Importante:** este archivo no debe subirse a Git.

---
## ⚙️ Configuración de Variables de Entorno
El archivo `.env` en la raíz del proyecto debe contener las siguientes variables para que el servicio de MongoDB funcione correctamente:

| Variable                  | Descripción                                               | Ejemplo              |
| ------------------------- | --------------------------------------------------------- | -------------------- |
| `ROOT_USERNAME`           | Nombre del superusuario de MongoDB (para la creación inicial). | `observer`           |
| `ROOT_PASSWORD`           | Contraseña del superusuario.                              | `0bserver123`        |
| `MONGO_APP_USER`          | Nombre de usuario para la aplicación (Python/Flask).      | `monitoreo_user`     |
| `MONGO_APP_PASSWORD`      | Contraseña para el usuario de la aplicación.              | `monitoreo_pass`     |

---
## 🚀 Uso

**Requisito:** Tener Docker y Docker Compose instalados.

Para levantar el servicio de MongoDB junto con el resto de la aplicación, ejecuta el siguiente comando desde la **raíz del proyecto**:

```bash
# Levanta todos los servicios en segundo plano
docker-compose up -d