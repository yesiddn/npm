# NPM: Gestión de paquetes y dependencias en JavaScript

## Historia

- **1995** - Nacimiento de `JavaScript` --> Uno de los lenguajes mas populares con miles de aplicaciones y grandes empresas apostando por este recurso.
- **2009** - Nace `Node.js` --> Un entorno en tiempo de ejecucion multiplataforma.
- **2009** - `NPM` (Node Package Manager) --> Gestor de paquetes por defecto para `Node.js`

## ¿Qué son los gestores de dependencias?

Organizan, administran y tienen una serie de herramientas las cuales podemos aprovehar en nuestros proyectos y ser mucho mas agiles en la creación de nuestras aplicaciones.

## Paquetes y modulos

Van a ser instalados y utlizados segun sea el caso. Podemos tener paquetes que funcionan solamente de lado de `Node` asi como tambien de lado de la `arquitectura web`.

## Herramientas que tenemos al instalar _`Node.js`_

- Repositorios online --> Podemos publicar paquetes que sean mejoras y/o ayudas para la construccion de aplicaciones.
- Command Line Client (CLI) --> Cliente que nos ayuda a trabajar de manera correcta con comandos.

## Cómo estructurar un archivo de configuración _`package.json`_

El archivo `package.json` es un **archivo de configuración que contiene la información más importante de tu proyecto** como: datos específicos, dependencias, dependencias de desarrollo y archivos de ejecución.

Este archivo, como su extensión lo indica, está estructurado en formato **`JSON` (JavaScript Object Notation)** que sirve para una mejor lectura e interpretación para los usuarios y las máquinas.

### Datos específicos del archivo _`package.json`_

Los datos específicos ayudan a identificar el proyecto y actúan como una base para que los usuarios y los contribuidores obtengan **información sobre el proyecto**.

El archivo `package.json` estaría estructurado inicialmente por las siguientes propiedades:

- **`"name"`:** Indica el **nombre** del proyecto.
- **`"version"`:** Indica la **versión** del proyecto.
- **`"description"`:** Indica una breve **descripción** del proyecto.
- **`"main"`:** Indica el **archivo principal** del proyecto. Por defecto es `index.js`.
- **`"scripts"`:** Indica los **comandos** a ejecutar del proyecto (no te preocupes por el comando test por ahora).
- **`"keywords"`:** Indica las **palabras clave** del proyecto.
- **`"author"`:** Indica el nombre y dirección de correo electrónico del **propietario** del proyecto. La estructura por convención es: `"nombre <email>"`.
- **`"license"`:** Indica la **licencia** del proyecto. La más común es `MIT`.

El archivo `package.json` estaría estructurado de la siguiente manera:

```json // archivo package.json
{ 
  "name": "npm", 
  "version": "1.0.0", 
  "description": "Constuir un paquete para node", 
  "main": "src/index.js", 
  "scripts": { 
    "test": "echo \"Error no test specified\" && exit 1" 
  }, 
  "keywords": [ "javascript", "node", "package" ], 
  "author": "TuNombre <tucorreo@gmail.com>", 
  "license": "MIT"
}
```

### Cómo utilizar el comando _`npm init`_

Aunque puedes crear el archivo de configuración manualmente, **NPM te ayuda a crearlo rápidamente mediante el comando `npm init`**. Este comando te permite ingresar los datos específicos del proyecto y genera el archivo `package.json` en tu directorio.

```bash
npm init
```

> - This utility will walk you through creating a `package.json` file. It only covers the most common items, and tries to guess sensible defaults.
> - See `npm help init` for definitive documentation on these fields and exactly what they do.
> - Use `npm install <pkg>` afterwards to install a package and save it as a dependency in the package.json file.
> - Press ^C at any time to quit. package name: (npm)

Puedes ingresar tus propios datos, o utilizar la recomendación de NPM (lo que está entre paréntesis) y solamente dar `Enter`. Al final, te preguntará si la configuración del `package.json` es correcta para generar el archivo.

```bash
version: (1.0.0) 
description: Constuir un paquete para node 
entry point: (index.js) src/index.js 
test command: npm test 
git repository: 
keywords: javascript, node, package 
author: TuNombre <tucorreo@gmail.com>
license: (MIT) 

About to write to /npm/package.json:

{ 
  "name": "npm", "version": "1.0.0", 
  "description": "Constuir un paquete para node", 
  "main": "src/index.js", 
  "scripts": { "test": "echo \"Error no test specified\" && exit 1" },
  "keywords": [ "javascript", "node", "package" ], 
  "author": "TuNombre <tucorreo@gmail.com>", 
  "license": "MIT" 
}

Is this OK? (yes) 
```

### Cómo utilizar el comando `npm init --yes`

El comando `npm init --yes` o `npm init -y` te ayudará a crear un archivo `package.json` de manera rápida con una **configuración por defecto**, sin la necesidad de ingresar los datos.

Para establecer esta configuración por defecto, necesitarás utilizar el comando `npm config set init-<atributo>`. Te comparto algunas de las configuraciones por defecto más comunes:

```bash
npm config set init-author-name "Tu Nombre" 

npm config set init-author-email "TuEmail@email.com" 

npm config set init-author-url "https://tuWeb.com" 

npm config set init-license "MIT" 

npm config set init-version "0.0.1"
```

De esta manera ya estás listo para gestionar dependencias de tu proyecto con NPM.

## Instalación de dependencias

Las dependencias son paquetes que vamos a utilizar en nuestro proyecto. **Un paquete es el conjunto de módulos para resolver un problema.** Saber manejar las dependencias en un proyecto permite desarrollar la aplicación más rápido sin partir desde cero.

Existen tres tipos de dependencias: **locales**, **desarrollo** y **globales**.

### Qué son las dependencias locales

Las dependencias locales son aquellas que son obligatorias para el proyecto, es decir, son las necesarias para que la aplicación funcione en producción. Producción significa que tu aplicación está disponible para usarse.

Para instalar una dependencia local, utiliza uno de los siguientes comandos.

#### Cómo instalar dependencias locales

```bash
npm install <paquete> 
npm install --save <paquete> 
npm install -S <paquete>
```

Las dependencias locales se encuentran en el `package.json` en la propiedad "**dependencies**", seguido de la versión que fue instalada.

```json
{ 
  ...

  "dependencies": { 
    "paquete": "^1.0.0" 
  },

  ...
}
```

### Qué son las dependencias de desarrollo

Las dependencias de desarrollo son aquellas que **no son obligatorias para el proyecto**, es decir, sin estas la aplicación servirá. Estas dependencias ofrecen una ayuda para construir código de forma óptima, por ejemplo, formatear el código, agregar estilos, levantar un servidor para observar los cambios.

#### Cómo instalar dependencias de desarrollo

Para instalar una dependencia de desarrollo, utiliza el siguiente comando.

```bash
npm install --save-dev <paquete> 
npm install -D <paquete>
```

Las dependencias de desarrollo se encuentran en el `package.json` en la propiedad "**dev-dependencies**", seguido de la versión que fue instalada.

```json
{ 
  ...

  "dev-dependencies": { 
    "paquete": "1.0.0" 
  } 
  
  ...
}
```

### Qué son las dependencias globales

Las dependencias globales son aquellas que están **disponibles para todos los proyectos en tu computador**, pero no aparecen el archivo de configuración `package.json`.

#### Cómo instalar dependencias globales

Para instalar una dependencia global, utiliza el siguiente comando.

```bash
npm install --global <paquete> 
npm install -g <paquete>
```

**Ten en cuenta que para instalar dependencias globales requiera permisos elevados**, esto se soluciona con la palabra reservada sudo en terminales basadas en Unix, o en Windows ejecutando la terminal como administrador. Puedes revisar este artículo: [Resolving EACCES permissions errors when installing packages globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) para evitar dar permisos cada vez que instalas una dependencia global.
package.json
**Las dependencias globales no se encuentran en el `package.json`**, por esta razón recomiendo no abusar de esta herramienta, ya que el archivo de configuración es muy importante para que otros desarrolladores tengan toda la información pertinente al proyecto, incluyendo las dependencias a utilizar.

#### Cómo visualizar los paquetes instalados

Para ver qué dependencias locales están instaladas, ejecuta el siguiente comando:

```bash
npm list
```

Para ver qué dependencias globales están instaladas, ejecuta uno de los siguientes comandos:

```bash
npm list -g 
npm list -g --depth 0
```

Puedes utilizar el flag `--depth` para indicar la profundidad de dependencias, esto mostrará los paquetes que contiene cada paquete.

```bash
npm list --depth 2
```

## Instalación de dependencias de versión específica

En ciertas situaciones es necesario instalar **una versión específica de un paquete**, ya sea porque el proyecto no puede actualizarse a versiones recientes, o porque el equipo necesita trabajar sobre una misma versión. Saber instalar cualquier versión de un paquete es fundamental para la gestión de dependencias de tu proyecto.

### Cómo instalar una versión específica de un paquete

Para **instalar una versión exacta** de una dependencia, utiliza el siguiente comando, donde es el nombre del paquete y es la versión exacta.

```bashpackage.json
npm install <paquete>@<versión>
```

También puedes usar la versión `latest` para asegurarte que está instalando la última versión disponible del paquete.

```bash
npm install <paquete>@latest
```

Este comando instalará la versión exacta del paquete desde el repositorio de NPM. Esto sirve para manejar diferentes versiones del paquete instalado donde sea compatible con el proyecto actual y no provoque errores.

Por ejemplo:

```bash
npm install json-server@0.15.0
```

### Cómo instalar dependencias opcionales

Las dependencias opcionales son aquellas que **no son obligatorias para el proyecto**, es decir, sin estas la aplicación servirá. Estas dependencias ofrecen una ayuda para construir código de forma óptima, por ejemplo, formatear el código, agregar estilos, levantar un servidor para observar los cambios.

Para instalar una deppackage.jsonendencia opcional, utiliza el siguiente comando.

```bash
npm install --save-optional <paquete> 
npm install <paquete> -O
npm install -O <paquete>
```

Ten en cuenta la `O` mayúscula, si utilizas la `o` minúscula, el paquete se instalará como dependencia local.

Las **dependencias opcionales** se encuentran en el `package.json` en la propiedad `"optionalDependencies"`, seguido de la versión que fue instalada.

```json
{ 
  ...
  
  "optionalDependencies": { 
    "paquete": "1.0.0" 
  } 

  ...
}
```

### Simular la instalación de una dependencia

Se pueden generar conflictos de dependencias cuando se instala un paquete, ya sea porque la versión no es compatible con el proyecto o porque el paquete depende de otro paquete que ya está instalado en el proyecto. Para evitar estos conflictos, es importante simular la instalación de una dependencia antes de instalarla en el proyecto.

Para simular la instalación de una dependencia, utiliza el siguiente comando.

```bash
npm install --dry-run <paquete>
npm install <paquete> --dry-run
```

Este comando mostrará el resultado de instalación sin instalarlo en el proyecto.

Por ejemplo:

```bash
npm i react --dry-run

added 4 packages in 2s

23 packages are looking for funding run npm fund for details
```

### Cómo funciona el comando npm install

El archivo `package.json` contiene la información de las dependencias del proyecto, pero si no tienes instaladas esas dependencias, **la manera para instalarlas todas en un solo comando es `npm install` o la forma corta `npm i`**. De este modo, instalarás cada paquete con su respectiva versión indicada en el `package.json`.

Si únicamente tenías el archivo `package.json` después de ejecutar el comando, aparte de instalar todas las dependencias, **se generará un archivo `package-lock.json` y un directorio llamado `node_modules`**.

**El archivo `package-lock.json` muestra todo el árbol de dependencias de tu proyecto**. ¿Qué significa esto? Cada dependencia instalada también tiene sus respectivas dependencias, a estas se las denomina **sub-dependencias**. El árbol de dependencias muestra todas las **sub-dependencias** como si de ramas se tratasen.

**El directorio `node_modules` contiene todos los archivos ejecutables de `Nodejs` y los módulos que contiene cada dependencia**. Este directorio es ignorado por los repositorios de Git, por eso es importante el archivo `package.json`, ya que te permitirá instalar las dependencias con `npm install` cuando realices un `fork` de cualquier repositorio.

## Comandos en NPM (Scripts)

El apartado de `"scripts"` en el `package.json` es el que **indica los comandos a ejecutar del proyecto**. Esta sección es la que utilizarás para crear comandos que optimicen el desarrollo de tu aplicación.

### Cómo crear un comando en tu proyecto

Para crear un comando en tu proyecto, utiliza la siguiente estructura, donde el nombre del comando debería ser muy descriptivo sobre lo que hace.

```json
{ 
  "scripts": { 
    "<nombre>": "<comando>" 
  } 
}
```

Una vez hayas escrito el comando en el archivo `package.json`, la manera de ejecutarlo en la terminal será con el comando `npm run <nombre>`.

#### Creemos algunos comandos comunes

Creemos tres comandos comunes: para iniciar el proyecto (`start`), crear un archivo para producción (`build`) y combinarlos (`deploy`). Que no te preocupe si no entiendes cada comando, **solo entiende cómo ejecuta NPM el script**.

```json
{ 
  "scripts": { 
    "start": "webpack-dev-server --open --mode development", 
    "build": "webpack --mode production", 
    "deploy": "npm run format && npm run build" 
  }
}
```

Y para ejecutarlos, es necesario utilizar el comando respectivo en la terminal:

```bash
npm run start

npm run build 

npm run deploy
```

NPM provee algunos **alias**, como `npm start` que ejecuta lo mismo que `npm run start`.

### Cómo ejecutar un paquete de manera directa (npx)

NPM te permite instalar paquetes en tu proyecto haiendo uso de **NPX (Node Package Execute)**

![NPX](https://static.platzi.com/media/user_upload/npm-npx-2e824100-77fb-49a5-904c-8713f1d4b5e5.jpg)

Sin embargo, **NPX** permite ejecutar un comando de NPM remotamente, ejemplos de este comportamiento son los paquetes **React** y **Nextjs**, para iniciar un proyecto en estos se puede ejecutar los siguientes comandos:

```bash
npx create-react-app <nombre-proyecto>

npx create-next-app <nombre-proyecto>
```

## Actualización de dependencias

Conocer cómo actualizar dependencias es muy importante para **mantener tus proyectos actualizados y libres de vulnerabilidades de seguridad**.

**El comando `npm outdate` mostrará los paquetes que están desactualizados**. Con el comando `npm outdate --dd` verás de manera más detallada esta información.

### Cómo actualizar dependencias

Para actualizar todas las dependencias utiliza el siguiente comando:

```bash
npm update
```

Ten en cuenta que **actualizar varios paquetes no es recomendable**, solamente deberías actualizar un paquete si estás muy seguro de que no afectará al proyecto y que realizaste los cambios pertinentes.

```bash
npm update <paquete>
```

Utiliza el siguiente comando para actualizar a la última versión (latest) de la dependencia.

```bash
npm install <paquete>@latest
```

## Seguridad y solución de problemas

**La seguridad de tu proyecto puede ser vulnerada por paquetes desactualizados**. Al momento de instalar tus paquetes con el comando `npm install` muestra una serie de advertencias (_**NPM WARN**_) de las dependencias desactualizadas.

### Auditar tus dependencias

El comando `npm audit` muestra una descripción de las dependencias instaladas. Si se encuentran vulnerabilidades, se calculará el impacto al proyecto .

Si se requiere un informe más detallado en formato JSON (JavaScript Object Notation), utiliza el comando `npm audit --json`.

El comando `npm audit fix` proporciona una actualización de los paquetes, similar al comando `npm update <paquete>`. El comando `npm audit fix --force` proporciona una actualización de los subpaquetes de cada paquete, en todos sus niveles de profundidad.

Si el problema persiste, es necesario actualizar el paquete a su última versión.

```bash
npm install <paquete>@latest
```

### Solución de problemas

Cuando estés **desarrollando un proyecto con NPM**, puede que generes errores que no permitan seguir con tu trabajo. **Saber manejar los errores es fundamental para solucionarlos y seguir con tus tareas** (y no entrar en pánico). Alguno de estos errores pueden ser:

- Errores en la configuración del archivo `package.json`
- Errores de dependencias en `node_modules`
- Errores del sistema operativo
- Configuración errónea de `Git` o `GitHub`
- Errores de escritura (typos)
- Errores que no estén ligados directamente a `NPM`

### Error de dependencias en node_modules

**Existen situaciones en las que instalas una dependencia con una versión que no corresponde a la deseada**. Esto ocurre porque `NPM` guarda en el caché una versión previamente instalada de un paquete, esto para mejorar los tiempos de instalación.

En esta situación, puedes utilizar los siguientes comandos, el primero para **borrar el caché de `NPM`** y el segundo para **verificar si están eliminados correctamente**.

```bash
npm cache clean --force 
npm cache verify
```

## Eliminación de dependencias y Packahe Lock

Conocer cómo eliminar dependencias, también es importante para mantener **tus proyectos sin paquetes que no aporten la solución a tu problema, que ya no sean actualizados, o que exista una mejor implementación.**

### Cómo eliminar paquetes

Existen dos formas de eliminar paquetes:

- Eliminando el paquete con el siguiente comando:

```bash
npm uninstall <paquete>
```

- Eliminarlo manualmente del archivo `package.json`. Al eliminar un paquete de manera manual, es necesario actualizar el directorio de `node_modules`.

#### Cómo actualizar el directorio de `node_modules`

Actualizar el directorio `node_modules` sirve para limpiar las dependencias que previamente estaban en el proyecto. También cuando existe algún archivo corrupto o una mala instalación.

Por lo tanto, deberás eliminar el directorio de `node_modules` y después ejecutar el comando `npm install` para instalar correctamente los paquetes. En ciertas situaciones, también es necesario eliminar el archivo `package-lock.json`.

Puedes utilizar el siguiente comando de **NPM** para evitar escribir demasiado cada vez que lo necesites.

```json
// package.json
{ 
  "scripts": { 
    "phoenix": "rm -f package-lock.json && rm -rf ./node_modules && npm i --no-fund --no-audit" 
  } 
}
```

### Mostrar los pasos ejecutados por un comando de **NPM**

Para identificar el error que puede existir en tu proyecto, es necesario analizar cada paso que ejecuta un comando, para saber en qué punto específico ocurre el problema.

El flag `--dd` en un comando de **NPM**, te mostrará de manera detallada cada paso ejecutado. De esta manera podrás observar si existe un error para solucionarlo.

```bash
npm [comando] --dd
```

Otra forma, es ejecutar el comando de **NPM**. Si existe un error, la terminal te mostrará los diferentes errores que encontró.

![Errores en comandos de NPM](https://static.platzi.com/media/articlases/Images/npm03.png)

```bash
npm run buld --dd
```

### Qué es el archivo `package-lock.json`

**El archivo `package-lock.json` describe todo el árbol de dependencias de cada paquete instalado.**

Cuando alguien hace **fork** de un repositorio no tiene el directorio `node_modules` por el archivo `.gitignore`. Mediante el comando `npm install`, instalarán las dependencias indicadas en el `package.json` con la versión indicada. También, se instalarán las **sub-dependencias** indicadas en `package-lock.json` con la versión indicada.

Esto es importante para tener instaladas siempre la versión adecuada del paquete a utilizar en el proyecto.

### Ver las dependencias deprecated

**Las dependencias deprecated son aquellas que ya no son mantenidas por el desarrollador**. Esto significa que no se actualizarán más, por lo tanto, no se corregirán errores ni vulnerabilidades de seguridad.

> **Nota:** En el contexto de la programación es común encontrarse con código al que se denomina deprecated. Basicamente el autor esta diciendo:
>> _"Esto que te ofrezco sigue funcionando, pero yo ya no me responsabilizo de que siga haciéndolo en un futuro, así que úsalo bajo tu propia responsabilidad (y no llores si deja de funcionar)."_

También llamado `npm clean install`. Este comando es similar al comando npm install. Con la diferencia que está pensado para ser utilizado en ambientes automatizados.

Por ejemplo. Plataforma de pruebas, integración continua o cualquier otra situación que se requiera realizar una instalación limpia de las dependencias.

Las principales diferencias entre install y ci se listan [aquí](https://docs.npmjs.com/cli/v8/commands/npm-ci).

## Creación de paquetes

Al crear un paquete para **NPM**, podrás compartir tu trabajo a varios desarrolladores e instalar tu paquete mediante `npm install <tuPaquete>`.
Te mostraré un ejemplo, un proyecto de mensajes aleatorios que estará instalado globalmente y se ejecutará mediante la terminal.

### Cómo colocar un nombre a tu paquete

Al publicar un paquete, **es necesario que el nombre sea único**, es decir, no debe existir ningún otro paquete publicado con el mismo nombre en **NPM**.

Sin embargo, **no agregues números**, ya que **NPM** lo detecta como spam. Es **válido agregar tu nombre de usuario** para diferenciarlo.

Asegúrate de eso buscando en la página oficial de **NPM** el nombre del paquete, si no hay coincidencias lo puedes publicar.

### Proyecto de mensajes aleatorios

Como buena práctica, crea un repositorio remoto en GitHub y clónalo en tu computador. Después, inicia un proyecto con **NPM** con el comando `npm init -y`. Con esto ya tienes todo listo para empezar el proyecto.

Dentro del proyecto crea la siguiente estructura de archivos:

- Un directorio llamado `src` que contenga el archivo principal del proyecto `index.js`.
- Un directorio llamado `bin` que contenga un archivo ejecutable `global.js`.
![Directorio base](https://static.platzi.com/media/user_upload/2021-02-26_13h37_38-ec2d49a5-4a2d-45ed-85e0-3b3e1c57ab91.jpg)

### Creando el archivo _`index.js`_

En el archivo `index.js` agrega el siguiente código:

- Un array llamado `messages` que contiene los mensajes.
- Una función `funnyCommit` que mostrará de manera aleatoria los elementos del array, es decir, los mensajes aleatorios.
- Al final, exporta la función mediante `module.exports`.

```js
const messages = [
  "This is where it all begins...",
  "Commit committed",
  "Version control is awful",
  "COMMIT ALL THE FILES!",
  "The same thing we do every night, Pinky - try to take over the world!",
  "Lock S-foils in attack position",
  "This commit is a lie",
  "I'll explain when you're older!",
  "Here be Dragons",
  "Reinventing the wheel. Again.",
  "This is not the commit message you are looking for",
  "Batman! (this commit has no parents)",
];

const funnyCommit = () => {
  const message = messages[Math.floor(Math.random() * messages.length)];
  console.log(`\x1b[34m${message}\x1b[89m`);
}

module.exports = {
  funnyCommit
};
```

### Creando el archivo _`global.js`_

En el archivo `global.js` agrega el siguiente código, en el que importamos la función del archivo `index.js` y la ejecutamos.

```js
!/usr/bin/env node
let random = require('../src/index.js');

random.funnyCommit();
```

La diferencia entre un módulo `local` y un módulo `global` es que el `local` **se guarda DENTRO de la carpeta del proyecto**, por lo cual, si quieres ejecutar el script en una terminal, tendrás que viajar primero a la carpeta.

El `global`, en cambio, **lo guarda en un path “universal”** (tú mismo puedes personalizarlo) el punto es que puedes ejecutar los scripts de este módulo sin importar en dónde estés ubicado dentro de tu terminal.

Según he leído, se recomienda siempre mantener módulos locales para evitar bugs tremendos de compatibilidad entre tus proyectos y realmente son pocos los módulos que merecen la pena trabajar globales, solo aquellos que te brindan comandos de terminal que frecuentes mucho o que uses en la mayoría de tus proyectos, de resto, es mejor manejar módulos locales.

`#!/usr/bin/env node` es una instrucción que sirve para indicar que este archivo se ejecutará con `Nodejs`. Después realizamos la importación de nuestro archivo `index.js`. Finalmente, ejecutamos la función de mensajes aleatorios `funnyCommit`.

### Modificar el archivo `package.json` para el proyecto

En el archivo `package.json`, agrega **"bin"**, haciendo referencia a nuestro archivo `global.js` y **"preferGlobal"** en `true`.

```js
{
  ...
  "bin": {
    "<nombre-proyecto>": "./bin/global.js"
  },
  "preferGlobal": true
}
```

El nombre que especifiquemos dentro de **"bin"** será el que utilicemos en la terminal cuando el paquete esté instalado.

**¡Listo! Ya tienes un paquete para publicarlo en NPM.**

## Publicación de paquetes

Antes de publicar el proyecto de mensajes aleatorios, debes asegurarte de que el paquete funcione correctamente.

### Cómo utilizar el comando _`npm link`_

El comando `sudo npm link` crea un enlace simbólico para reconocer este paquete dentro del listado de NPM, **sin publicarlo todavía.**

Si no presenta errores, está listo para ser publicado.

### Cómo simular la instalación de tu paquete

Para simular la instalación de tu paquete de manera local, identifica el directorio en el que te encuentras con el comando `pwd`, **debe ser el mismo del proyecto**.

Después, ejecuta `npm install -g <ruta>`, donde la ruta es del directorio de tu proyecto. Esto sirve para instalarlo de manera global.

```bash
sudo npm install -g /Users/tuUsuario/tu-paquete
```

De esta manera, ya puedes ejecutar el programa con el comando que creamos en `"bin"`, `random-str-msg` y funcionará de forma global en el sistema.

```bash
random-str-msg
/* Output
Commit committed
*/

random-str-msg
/* Output
Here be Dragons
*/
```

### Cómo publicar un paquete en NPM

Una vez revisado que el paquete funcione correctamente, debes asegurarte de cumplir con los siguientes requisitos:

- Asegurar que el programa funcione reduciendo en lo posible los _bugs_.
- Revisar que la configuración del archivo `package.json` sea correcta.
- Tener un nombre único para el proyecto, usando guiones (-) para separar palabras y evitando números.
- [Crear una cuenta](https://www.npmjs.com/signup) en **NPM**, ya que aquí estarán tus paquetes a tu nombre. Después, debes utilizar el comando `npm adduser` para iniciar sesión en la terminal. Llena los datos, si no aparece tu contraseña, no te preocupes, es una forma de seguridad.

Una vez hayas cumplido los requisitos, **ejecuta el comando `npm publish`** y si no existen errores, tu paquete será publicado.

#### Validar con qué usuario publicar un paquete en NPM

Para **validar el usuario** con el que publicarás un paquete en **NPM**, debes utilizar el comando `npm whoami` para visualizar el usuario actual, **esto es importante si tienes varias cuentas de NPM**.

## Versionado de paquetes y paquetes privados

El versionado semántico consiste en la estructura que debemos seguir para colocar una versión a nuestro paquete.

### Qué es el versionado semántico

El versionado semántico está conformado por tres valores:

- **Major:** el valor que muestra la versión que contiene los cambios importantes del paquete.
- **Minor:** el valor que muestra la versión que contiene los cambios en funcionalidades, pero no representan un cambio significativo.
- **Patch:** el valor que muestra la versión que contiene cambios rápidos para solucionar problemas de seguridad o _bugs_.

![Versionado de paquetes en NPM](https://static.platzi.com/media/user_upload/wheelbarrel-no-tilde-caret-white-bg-w1000-72ca1a72-4c7f-4abe-8482-425c01a72f89.jpg)

#### Símbolos ^ y ~ para actualizar las versiones minor y patch

**Existen dos símbolos que acompañan al versionado sirven para actualizar las versiones _minor_ y _patch_ del paquete.**

- **Caret (^):** Permite actualizar las versiones _minor_ y _patch_.
- **Tilde (~):** Permite actualizar las versiones _patch_.

Por ejemplo, tenemos la versión `5.2.3`:

- Si tiene el _carret_ `^5.2.3`, actualizará la versión _minor_ y _patch_, por lo que tendrás versiones como `^5.3.3`, `^5.4.3`, `^5.4.4`, y así sucesivamente. Pero no versiones mayores a `6.0.0`.
- Si tiene la _tilde_ `~5.2.3`, actualizará la versión de _patch_, por lo que tendrás versiones como `~5.2.4`, `~5.2.5`, `~5.2.6`, y así sucesivamente. Pero no versiones mayores a `5.3.0`.

#### Buenas prácticas en el versionado de paquetes

**Lo recomendable es eliminar estos símbolos y tener la versión exacta** (sin símbolos) para evitar problemas de versionado, principalmente con paquetes que los mantienen pocas personas o no son fiables.

Debes manejar las actualizaciones cuando sea pertinente y asegurándote que no entrará en conflicto la nueva versión con la antigua.

### Cómo realizar cambios a la versión de tu paquete de NPM

**Si realizas cambios en tu código, tienes que cambiar la versión de tu paquete.** Debes utilizar los siguientes comandos, según la versión que desees cambiar:

```bash

## Aumenta una version path (1.0.0) -> (1.0.1)

$ npm version patch

## Aumenta una version minor (1.0.0) -> (1.1.0)

$ npm version minor

## Aumenta una version major (1.0.0) -> (2.0.0)

$ npm version major

## Aumenta una version específica (1.0.0) -> (3.1.1)

$ npm version 
```

Una vez actualizada la versión de tu paquete, puedes ejecutar nuevamente el comando `npm publish` para actualizarlo en los repositorios de NPM.

### Paquetes privados

Para usar paquetes privados necesitas:

- Una versión igual o superior a la 2.7.0 de NPM.
- Tener una cuenta de **usuario u organización de pago**.

En un paquete privado de NPM, solo pueden participar el propietario y los colaboradores autorizados. De esta manera, puedes seguir construyendo el paquete con una combinación de **código privado y dependencias públicas**.

### Actualizar tu paquete en NPM con buenas prácticas

Tu paquete debe contener toda la información posible para que el usuario puede instalarlo, utilizarlo y hasta colaborar para solucionar posibles _bugs_. Por ende, **es necesario que tengas configurado, por lo menos, un archivo `README.md`** y un repositorio remoto (GitHub, GitLab, etc.).

Una vez tengas estos requisitos, puedes actualizar tu paquete a una nueva versión, luego publícalo nuevamente.

#### Cómo crear un archivo _README.md_ para tu paquete

Para crear un archivo _README.md_ puedes utilizar esta [estructura base](https://gist.github.com/gndx/1b2c8482049c6d3b521dffcf33337558) y adecuarla a tu proyecto. Puedes ver el código haciendo clic en el botón "Raw".
