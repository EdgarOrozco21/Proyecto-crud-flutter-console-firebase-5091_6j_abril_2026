¡Excelente iniciativa! Integrar Firebase en una aplicación de Flutter te abre la puerta a bases de datos, autenticación, notificaciones y mucho más. Para lograrlo, el puente principal es **Firebase CLI** (Command Line Interface), y para instalarlo en Windows, la ruta más estándar y recomendada es a través de Node.js y su gestor de paquetes, npm.

Aquí tienes la guía paso a paso y directa al grano para configurar tu entorno en Windows.

---

### Software necesario: Entendiendo la relación Node.js y npm
No necesitas descargar `npm` por separado. **npm (Node Package Manager)** viene empaquetado directamente dentro de la instalación de **Node.js**. Al instalar Node.js, automáticamente obtienes npm.

---

### 1. Cómo verificar si npm/Node.js está instalado y qué versión utilizar

Antes de instalar nada, abre tu consola de comandos en Windows (puedes usar el **Símbolo del sistema (cmd)** o **PowerShell**) y escribe los siguientes comandos, presionando *Enter* después de cada uno:

```bash
node -v
```
```bash
npm -v
```

* **Si están instalados:** Verás números de versión (ej. `v20.11.0` y `10.2.4`).
* **Si no están instalados:** Verás un error de Windows diciendo que el comando no se reconoce.
* **¿Qué versión utilizar?:** Siempre debes apuntar a la versión **LTS (Long Term Support)** de Node.js. Es la versión más estable, probada y recomendada para la mayoría de los usuarios y herramientas de desarrollo, incluyendo Firebase.

---

### 2 y 3. Instalación paso a paso de Node.js y npm (De manera global)

Si los comandos anteriores te dieron error, sigue estos pasos. En Windows, la instalación estándar de Node.js configura automáticamente npm para que funcione **de manera global** en todo tu sistema a través de las variables de entorno (PATH).

1.  **Descarga el instalador:** Ve a la página oficial [nodejs.org](https://nodejs.org/).
2.  **Selecciona la versión LTS:** Haz clic en el botón grande que dice **"LTS"** (Recomendado para la mayoría). Esto descargará un archivo `.msi` para Windows.
3.  **Ejecuta el instalador:** Abre el archivo descargado.
4.  **Sigue el asistente (Next, Next, Next):** Acepta los términos de licencia.
5.  **Paso CRÍTICO (Add to PATH):** En la pantalla de "Custom Setup" (Configuración personalizada), asegúrate de que la opción **"Add to PATH"** (Agregar al PATH) esté habilitada. Esto es lo que permite que Node y npm se ejecuten globalmente desde cualquier carpeta en tu consola. Por defecto, el instalador ya la deja activada.
6.  **Instalación de herramientas adicionales:** Opcionalmente, te preguntará si quieres instalar herramientas para módulos nativos (Chocolatey, Python, etc.). Para Firebase CLI no es estrictamente necesario, pero puedes marcarlo si planeas desarrollar en Node.js a futuro.
7.  **Finaliza e instala:** Haz clic en *Install*.
8.  **Reinicia tu consola:** Si tenías una consola abierta, ciérrala y abre una nueva para que reconozca los nuevos comandos globales. Vuelve a ejecutar `node -v` y `npm -v` para confirmar.

---

### 4. Cómo utilizar los comandos de Firebase CLI

Una vez que Node.js y npm están instalados y reconocidos globalmente por tu sistema, es hora de instalar las herramientas de Firebase.

#### A. Instalar firebase-tools
En tu consola, ejecuta el siguiente comando:

```bash
npm install -g firebase-tools
```
* **`npm install`**: Le dice a npm que quieres descargar un paquete.
* **`-g`**: Es la bandera clave. Significa **"Global"**. Instalará Firebase CLI en tu sistema, permitiéndote usar el comando `firebase` en cualquier carpeta o proyecto de Flutter que tengas.
* **`firebase-tools`**: Es el nombre oficial del paquete de Google en el registro de npm.

#### B. Acceder a Firebase con tu Cuenta de Google
Una vez que termine la instalación, necesitas vincular la consola con tu cuenta para que tenga permiso de modificar tus proyectos.

1.  Escribe el siguiente comando en la consola:
    ```bash
    firebase login
    ```
2.  **Recolección de datos:** Es posible que la consola te pregunte si deseas permitir que Firebase recopile información anónima de uso (CLI usage and error reporting). Escribe `Y` (Sí) o `n` (No) y presiona Enter.
3.  **Apertura del navegador:** Se abrirá automáticamente una pestaña en tu navegador web predeterminado.
4.  **Selecciona tu cuenta:** Elige la cuenta de Google con la que creaste tu proyecto en la consola web de Firebase.
5.  **Concede permisos:** Haz clic en "Permitir" para darle acceso a Firebase CLI.
6.  **¡Éxito!:** El navegador mostrará un mensaje de éxito ("Firebase CLI Login Successful"). Puedes cerrar esa pestaña, volver a tu consola de Windows y verás un mensaje como: `Success! Logged in as tu_correo@gmail.com`.

**Siguiente paso para Flutter:**
Como estás trabajando con Flutter, una vez que `firebase login` esté listo, el siguiente paso en tu flujo de trabajo será instalar **FlutterFire CLI** (que usa el SDK de Dart) para enlazar automáticamente tu código de Flutter con la consola de Firebase. Eso lo harás con el comando: `dart pub global activate flutterfire_cli`.
