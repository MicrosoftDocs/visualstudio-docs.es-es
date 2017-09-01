---
title: JavaScript en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 04/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: wilkelly
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: d217443ed0231d71f861ed54b27f3f8d1e8d49ac
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="javascript-in-includevsdev15docsmiscincludesvsdev15mdmd"></a>JavaScript en [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)]

JavaScript es un lenguaje de primera clase en Visual Studio. Puede usar la mayoría de las ayudas de edición estándar (fragmentos de código, IntelliSense, etc.) al escribir código JavaScript en el IDE de Visual Studio. Puede escribir código JavaScript para muchos tipos de aplicaciones y servicios.

## <a name="ES6"></a> Compatibilidad con ECMAScript 2015 (ES6) y más allá
Visual Studio admite ahora la sintaxis para actualizaciones del lenguaje ECMAScript, como ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>¿Qué es ECMAScript 2015?

JavaScript sigue aún evolucionando como un lenguaje de programación y [TC39](http://www.ecma-international.org/memento/TC39.htm) es el comité responsable de realizar actualizaciones.  
ECMAScript 2015 es una actualización del lenguaje JavaScript que incorpora numerosa funcionalidad y sintaxis nuevas y de gran utilidad.
Para profundizar en las características de ES6, consulte [este](http://es6-features.org) sitio de referencia.

Además, para la compatibilidad con ECMAScript 2015, Visual Studio también admite ECMAScript 2016 y tendrá compatibilidad con versiones futuras de ECMAScript cuando se publiquen. Para mantenerse informado con TC39 y los últimos cambios en ECMAScript, siga su trabajo en [Github](https://github.com/tc39).

### <a name="transpiling-javascript"></a>Transpilación de JavaScript

Un problema común con JavaScript es que querrá usar las características de lenguaje ES6+ más recientes porque le ayudan a ser más productivo, pero sus entornos en tiempo de ejecución (con frecuencia exploradores) no admiten aún estas nuevas características.
Esto significa que tiene que mantener el seguimiento de qué exploradores admiten qué características (lo que puede ser pesado), o necesita una forma de convertir el código de ES6+ en una versión que sus entornos de ejecución de destino admitan (normalmente ES5).
Esto se conoce normalmente como "transpilación".

Una de las principales características de TypeScript es la posibilidad de transpilar código de ES6+ a ES5 o ES3, de forma que pueda escribir el código que le permita ser más productivo, pero seguir ejecutando el código en cualquier plataforma.  
Como JavaScript en [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] usa el mismo servicio de lenguaje que TypeScript, también puede aprovechar ES6+ para la transpilación de ES5.

Antes de que se pueda configurar, se requiere un cierto conocimiento de las opciones de configuración. TypeScript se configura mediante un archivo `tsconfig.json`. Si falta ese archivo, se usan algunos valores predeterminados. Por motivos de compatibilidad, estos valores predeterminados son diferentes en un contexto en que solo están presentes archivos JavaScript (y, opcionalmente, archivos `.d.ts`). Para compilar archivos de JavaScript, se debe agregar un archivo `tsconfig.json` y después se deben establecer de forma explícita algunas de estas opciones.

La configuración necesaria para el archivo tsconfig se describe a continuación:

 - `allowJs`: Este valor debe establecerse en `true` para que se reconozcan los archivos JavaScript.
De manera predeterminada es `false`, ya que TypeScript compila en JavaScript, y es necesario para evitar que el compilador incluya archivos que acaba de compilar.
 - `outDir`: Se debe establecer en una ubicación que no esté incluida en el proyecto, para que los archivos JavaScript emitidos no se detecten e incluyan en el proyecto (consulte `exclude` a continuación).
 - `module`: Si se usan módulos, esta opción le indica al compilador qué formato de módulo debería usar el código emitido (por ejemplo, `commonjs` para Node o software que instala varios programas como Browserify).
 - `exclude`: Esta opción indica qué carpetas no incluir en el proyecto. 
 La ubicación de salida, así como las carpetas que no son del proyecto, como `node_modules` o `temp`, deben agregarse a esta opción.
 - `enableAutoDiscovery`: Esta opción habilita la detección automática y la descarga de archivos de definición, como se ha descrito anteriormente.
 - `compileOnSave`: Esta opción indica al compilador si debe volver a compilar cada vez que se guarda un archivo de origen en Visual Studio.
 - `typeAcquisition`: este conjunto de valores controla el comportamiento de la adquisición automática de tipos (se explica con más detalle en [esta sección](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense#Auto))

Para convertir archivos de JavaScript en módulos de CommonJS y colocarlos en una carpeta `./out`, podría usar el siguiente archivo `tsconfig.json`.

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
  "typeAcquisition": {
    "enable": true
  }
}
```

Con la configuración anterior implementada, si un archivo de origen (`./app.js`) existía y contenía varias características del lenguaje ECMAScript 2015 tal y como se muestra a continuación:

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
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
```

## <a name="better-intellisense"></a>IntelliSense mejorado

JavaScript IntelliSense en [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] mostrará ahora mucha más información sobre las listas de parámetros y miembros. Esta nueva información la proporciona el servicio de lenguaje TypeScript, que usa el análisis estático en segundo plano para comprender mejor el código. Puede obtener más información sobre la nueva experiencia de IntelliSense y cómo funciona [aquí](/visualstudio/ide/javascript-intellisense/).

## <a name="JSX"></a> Compatibilidad con la sintaxis JSX

JavaScript en [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] tiene compatibilidad enriquecida con la sintaxis de JSX. JSX es un conjunto de sintaxis que admite etiquetas HTML en archivos JavaScript. 

La siguiente ilustración muestra un componente React definido en el archivo TypeScript `comps.tsx` y después este componente se usa desde el archivo `app.jsx`, completo con IntelliSense para las finalizaciones y documentación de las expresiones de JSX.
Aquí no es necesario TypeScript, este ejemplo concreto solo contiene algún código de TypeScript.

<img src="./media/react.png" height="500" width="640"/>

> [!NOTE]
> Para convertir la sintaxis JSX en llamadas React, debe agregarse la configuración `"jsx": "react"` a las `compilerOptions` del archivo `tsconfig.json` descrito anteriormente.

El archivo JavaScript creado en "./out/app.js" tras la compilación debería contener el código:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

# <a name="configuring-your-javascript-project"></a>Configuración del proyecto de JavaScript
El servicio de lenguaje funciona con análisis estático, lo que significa que analiza el código fuente sin ejecutarlo realmente para devolver resultados de IntelliSense y proporcionar otras características de edición.
Por lo tanto, cuanta mayor sea la cantidad y el tamaño de los archivos que se incluyen en el contexto del proyecto, más memoria y CPU se usarán durante el análisis.
Por este motivo, hay algunas suposiciones predeterminadas que se realizan sobre la forma del proyecto:

- `package.json` y `bower.json` muestran las dependencias usadas por el proyecto y se incluyen de forma predeterminada en la adquisición automática de tipos (ATA) <TODO - agregar vínculo>
- Una carpeta `node_modules` de nivel superior contiene el código fuente de la biblioteca y su contenido se excluye de forma predeterminada del contexto del proyecto.
- Cada uno de los demás archivos `.js`, `.jsx`, `.ts` y `.tsx` es posiblemente uno de *sus propios* archivos de origen y se debe incluir en el contexto del proyecto.

En la mayoría de los casos, podrá abrir su proyecto y tener una gran experiencia usando la configuración predeterminada anterior del proyecto.
Sin embargo, en proyectos con estructuras de carpeta diferentes o proyectos especialmente grandes, puede ser conveniente configurar el servicio de lenguaje para centrarse mejor únicamente en sus propios archivos de origen.

## <a name="overriding-defaults"></a>Invalidación de los valores predeterminados
Puede invalidar la configuración predeterminada anterior agregando un archivo `tsconfig.json` a la raíz del proyecto.
Un archivo `tsconfig.json` tiene varias opciones diferentes que se pueden manipular el contexto del proyecto.
Algunas de ellas se enumeran a continuación, pero para ver un conjunto completo de todas las opciones disponibles, [consulte el almacén de esquemas](http://json.schemastore.org/tsconfig). 

## <a name="important-tsconfigjson-options"></a>Opciones de `tsconfig.json` importantes

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA 
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

## <a name="example-project-configuration"></a>Ejemplo de configuración de proyecto

Dado un proyecto con la siguiente configuración:
- los archivos de origen del proyecto están en `wwwroot/js`
- los archivos lib están en `wwwrrot/lib`
- `bootstrap`, `jquery`, `jquery-validation` y `jquery-validation-unobtrusive` se muestran en el archivo `bower.json`
- `kendo-ui` se ha agregado manualmente a la carpeta lib

![Estructura de carpetas](./media/folderStructure.png)

Podría usar el siguiente archivo `tsconfig.json` para asegurarse de que el servicio de lenguaje solo analice los archivos de origen de la carpeta `js`, pero siga capturando y usando archivos `.d.ts` en las bibliotecas de la carpeta `lib`.

```json
{
  "compilerOptions": {
    "allowJs": true,          
    "noEmit": true            
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,            
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

# <a name="notable-changes-from-vs-2015"></a>Cambios importantes desde VS 2015 
Dado que [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] presenta un servicio de lenguaje completamente nuevo, hay algunos comportamientos que serán diferentes o que anterior.
Los cambios más importantes son el reemplazo de VSDoc por JSDoc, la eliminación de extensiones `.intellisense.js` personalizadas y la limitación de IntelliSense en algunos patrones de código específicos.

## <a name="no-more-references-or-referencesjs"></a>No más `///<references/>` o `_references.js`
Antes era bastante difícil entender en cualquier momento dado qué archivos estaban en el ámbito de IntelliSense.
En ocasiones, era recomendable tener todos los archivos en ámbito y otras veces no, pero esto llevaba a configuraciones complejas que implicaban la administración manuales de referencias.
En adelante, ya no necesita pensar en las administración de referencias, así que no necesita comentarios de referencias de tres barras diagonales o archivos `_references.js`.

Consulte la página [IntelliSense para JavaScript](/visualstudio/ide/javascript-intellisense/) para más información sobre el funcionamiento de IntelliSense.

## <a name="vsdoc"></a>VSDoc
Los comentarios de documentación XML, en ocasiones conocidos como VSDocs, podían usarse anteriormente para decorar el código fuente con datos adicionales que se usaban para pulir los resultados de IntelliSense.
VSDoc ya no se admite en favor de [JSDoc](http://usejsdoc.org/about-getting-started.html), que es más fácil de escribir y es el estándar aceptado para JavaScript.

### <a name="intellisensejs-extensions"></a>Extensiones de `.intellisense.js`
Anteriormente, podría crear [extensiones de IntelliSense](https://msdn.microsoft.com/en-us/library/hh874692.aspx), lo que le permitía agregar los resultados de finalización personalizados para bibliotecas de terceros.
Estas extensiones eran bastante difíciles de escribir e instalarlas y hacer referencia a ellas era complicado, así que desde ahora el nuevo servicio de lenguaje no admitirá estos archivos.
Como una alternativa más sencilla, puede escribir un archivo de definición de TypeScript para proporcionar las mismas ventajas de IntelliSense que las antiguas extensiones de `.intellisense.js`.
Puede aprender más sobre la creación de archivos (`.d.ts`) de declaración [aquí](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Patrones no admitidos
Dado que el nuevo servicio de lenguaje funciona con el análisis estático en lugar de con un motor de ejecución (lea [este problema](https://github.com/Microsoft/TypeScript/issues/4789) para más información de las diferencias), hay algunos patrones de JavaScript que ya no se pueden detectar.
El modelo más común es el patrón "expando". Actualmente, el servicio de lenguaje no puede proporcionar IntelliSense en objetos que tienen propiedades que se han agregado después de la declaración.
Por ejemplo:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Para solucionar este problema, puede declarar las propiedades durante la creación de objetos:
```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

También puede agregar un comentario JSDoc como se indicó anteriormente:
```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
