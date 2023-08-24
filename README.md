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
