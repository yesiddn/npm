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

```bash
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

Para instalar una dependencia opcional, utiliza el siguiente comando.

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
