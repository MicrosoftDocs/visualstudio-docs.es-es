---
title: IntelliSense para JavaScript | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
author: mikejo
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: d07820eda0d76163d99d7752789750eaf56182fd
ms.openlocfilehash: 1f8372fe201d6b23ee2c65e0f6d6a2fa28976654
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-intellisense"></a>IntelliSense para JavaScript
[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] proporciona una experiencia eficaz de edición de JavaScript lista para usar. Con tecnología de un servicio de lenguaje basado en TypeScript, Visual Studio proporciona IntelliSense con más funcionalidades, compatibilidad con características modernas de JavaScript y características de productividad mejoradas, como Ir a definición, la refactorización y mucho más.

> [!NOTE]
>  JavaScript Language Service en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] usa un nuevo motor para el servicio de lenguaje ("salsa"). Se incluyen detalles en este tema y es posible que también quiera leer esta [publicación de blog](https://blogs.msdn.microsoft.com/visualstudio/2016/04/08/previewing-salsa-javascript-language-service-visual-studio-15/). La nueva experiencia de edición se aplica también en gran parte a VS Code. Consulte [documentos de VS Code](https://code.visualstudio.com/docs/languages/javascript) para obtener más información.

Para obtener más información sobre la funcionalidad general de IntelliSense de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], consulte [Using IntelliSense](../ide/using-intellisense.md) (Usar IntelliSense). 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Novedades de JavaScript Language Service en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

- IntelliSense con más funcionalidades

    JavaScript IntelliSense en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] mostrará ahora mucha más información sobre las listas de parámetros y miembros.
Esta nueva información la proporciona el servicio de lenguaje TypeScript, que usa el análisis estático en segundo plano para comprender mejor el código.
TypeScript usa varios orígenes para generar esta información.
    - [IntelliSense basado en la inferencia de tipos](#TypeInference)
    - [IntelliSense basado en JSDoc](#JsDoc)
    - [IntelliSense basado en archivos de declaración de TypeScript](#TSDeclFiles)

- [Adquisición automática de definiciones de tipo](#Auto)
- [Compatibilidad con ES6 y más](#ES6)
- [Compatibilidad con la sintaxis JSX](#JSX)

## <a name="TypeInference"></a> IntelliSense basado en la inferencia de tipos
En JavaScript, la mayoría de las veces no hay ningún tipo explícito de información disponible. Afortunadamente, suele ser bastante fácil deducir un tipo según el contexto del código circundante.
Este proceso se denomina inferencia de tipos.

En el caso de una variable o propiedad, el tipo es normalmente el tipo del valor que se usa para inicializarla o la asignación de valor más reciente. 

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

En el caso de una función, el tipo de valor devuelto puede deducirse a partir de las instrucciones return. 

En el caso de parámetros de función, actualmente no hay ninguna inferencia, pero hay formas de solucionar este problema mediante archivos `.d.ts` de JSDoc o TypeScript (consulte las secciones posteriores).

Además, hay una inferencia especial para lo siguiente:
 - Clases de "estilo ES3", especificadas mediante una función de constructor y asignaciones a la propiedad de prototipo.
 - Patrones de módulo de estilo CommonJS, especificados como asignaciones de propiedad en el objeto `exports` o asignaciones a la propiedad `module.exports`.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

## <a name="JsDoc"></a> IntelliSense basado en JSDoc

Si la inferencia de tipos no proporciona la información de tipo deseada (o por compatibilidad con la documentación), se puede proporcionar información de tipo de forma explícita a través de anotaciones de JSDoc.  Por ejemplo, para proporcionar a un objeto parcialmente declarado un tipo específico, puede usar la etiqueta `@type` como se muestra a continuación:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Como se ha mencionado, los parámetros de función no se deducen nunca. En cambio, con la etiqueta `@param` de JSDoc, también puede agregar tipos a parámetros de función. 

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```
 
Consulte [este documento](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) para ver las anotaciones de JsDoc que se admiten actualmente.

## <a name="TsDeclFiles"></a> IntelliSense basado en archivos de declaración de TypeScript

Dado que TypeScript y JavaScript se basan ahora en el mismo servicio de lenguaje, pueden interactuar de manera más completa. Por ejemplo, se puede proporcionar IntelliSense para JavaScript para valores declarados en un archivo `.d.ts` ([más información](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md)), y los tipos como interfaces y clases que se declaran en TypeScript están disponibles para su uso como tipos en comentarios de JsDoc. 

A continuación, se muestra un ejemplo sencillo de un archivo de definición de TypeScript que proporciona esa información de tipo (a través de una interfaz) a un archivo JavaScript en el mismo proyecto (con una etiqueta de JsDoc).

_**Declaraciones de TypeScript usadas en JavaScript**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

## <a name="Auto"></a> Adquisición automática de definiciones de tipo
En el mundo de TypeScript, las bibliotecas más populares de JavaScript tienen sus API descritas mediante archivos `.d.ts` y el repositorio más común para esas definiciones se encuentra en [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

De manera predeterminada, el servicio de lenguaje Salsa intentará detectar qué bibliotecas de JavaScript están en uso. Además, descargará y hará referencia de forma automática al archivo `.d.ts` correspondiente que describe la biblioteca para proporcionar IntelliSense con más funcionalidades. Los archivos se descargan en una caché ubicada en la carpeta de usuario en `%LOCALAPPDATA%\Microsoft\TypeScript`. 

> [!NOTE]
> Esta característica está **deshabilitada** de manera predeterminada si usa un archivo de configuración `tsconfig.json`, pero se puede habilitar como se describe más adelante.

Actualmente, la detección automática funciona para las dependencias descargadas desde npm (al leer el archivo `package.json`), Bower (al leer el archivo `bower.json`) y para archivos separados en el proyecto que coinciden con una lista de aproximadamente las 400 bibliotecas de JavaScript más populares. Por ejemplo, si tiene `jquery-1.10.min.js` en el proyecto, el archivo `jquery.d.ts` se capturará y cargará para proporcionar una mejor experiencia de edición. Este archivo `.d.ts` no tendrá ningún impacto en el proyecto. 

Si no quiere usar la adquisición automática, puede deshabilitarla mediante la adición de un archivo de configuración como se describe a continuación. Aún puede colocar archivos de definición de forma manual para usarlos directamente en el proyecto.

## <a name="ES6"></a> Compatibilidad con ES6 y más

ES6, o ECMAScript 2015, es la siguiente versión de JavaScript. Aporta una nueva sintaxis al lenguaje, como clases, funciones de flecha, `let`/`const` y mucho más. Esta nueva sintaxis es compatible con Visual Studio.

Una de las características clave que ofrece TypeScript es la capacidad de usar características de ES6 y emitir código que se puede ejecutar en entornos en tiempo de ejecución de JavaScript que aún no comprenden esas características más recientes. Normalmente, esto se conoce como "transpilación". Dado que JavaScript usa el mismo servicio de lenguaje, también puede aprovechar ES6+ para la transpilación de ES5.

Antes de que se pueda configurar, se requiere un cierto conocimiento de las opciones de configuración.  TypeScript se configura mediante un archivo `tsconfig.json`. Si falta ese archivo, se usan algunos valores predeterminados. Por motivos de compatibilidad, estos valores predeterminados son diferentes en un contexto en que solo están presentes archivos JavaScript (y, opcionalmente, archivos `.d.ts`). Para compilar archivos JavaScript, se debe agregar un archivo `tsconfig.json` y después se deben establecer de forma explícita algunos de estos valores predeterminados.

La configuración necesaria para el archivo tsconfig se describe a continuación:

 - `allowJs`: Este valor debe establecerse en `true` para que se reconozcan los archivos JavaScript.
De manera predeterminada es `false`, ya que TypeScript compila en JavaScript, y es necesario para evitar que el compilador incluya archivos que acaba de compilar.
 - `outDir`: Se debe establecer en una ubicación que no esté incluida en el proyecto, para que los archivos JavaScript emitidos no se detecten e incluyan en el proyecto (consulte `exclude` a continuación).
 - `module`: Si se usan módulos, esta opción le indica al compilador qué formato de módulo debería usar el código emitido (por ejemplo, `commonjs` para Node o software que instala varios programas como Browserify).
 - `exclude`: Esta opción indica qué carpetas no incluir en el proyecto. 
 La ubicación de salida, así como las carpetas que no son del proyecto, como `node_modules` o `temp`, deben agregarse a esta opción.
 - `enableAutoDiscovery`: Esta opción habilita la detección automática y la descarga de archivos de definición, como se ha descrito anteriormente.
 - `compileOnSave`: Esta opción indica al compilador si debe volver a compilar cada vez que se guarda un archivo de origen en Visual Studio.

Para convertir archivos JavaScript en módulos de CommonJS en una carpeta `./out`, se pueden incluir opciones similares a las siguientes en un archivo `tsconfig.json`.

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typingOptions": {
    "enableAutoDiscovery": true
  }
}
```

Con la configuración anterior en su lugar, si un archivo de origen (`./app.js`) existía, contiene varias características del lenguaje ECMAScript 2015 tal y como se muestra a continuación:

```js
import {Subscription} from 'rxjs/Subscription';

class Foo {
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;
    }
}

export let sqr = x => x * x;
export default Subscription;
```

Entonces se emitiría un archivo a `./out/app.js` con ECMAScript 5 como destino (valor predeterminado) con un aspecto similar al siguiente:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
//# sourceMappingURL=app.js.map
```

## <a name="JSX"></a> Compatibilidad con la sintaxis JSX

JavaScript en Visual Studio 2017 ofrece una amplia compatibilidad con la sintaxis JSX. JSX es un conjunto de sintaxis que admite etiquetas HTML en archivos JavaScript. 

La siguiente ilustración muestra un componente React definido en el archivo TypeScript `comps.tsx` y después este componente se usa desde el archivo `app.jsx`, completo con IntelliSense para las finalizaciones y documentación de las expresiones de JSX.
Aquí no es necesario TypeScript, este ejemplo concreto solo contiene algún código de TypeScript.
<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/react.png" height="500" width="640"/>

> [!NOTE]
> Para convertir la sintaxis JSX en llamadas React, debe agregarse la configuración `"jsx": "react"` a las `compilerOptions` del archivo `tsconfig.json` descrito anteriormente.

El archivo JavaScript creado en "./out/app.js" tras la compilación debería contener el código:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

