---
title: IntelliSense para JavaScript
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de5470f0c48e76d972cd78fd84b7629b8f2426d2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849679"
---
# <a name="javascript-intellisense"></a>IntelliSense para JavaScript

[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] proporciona una experiencia eficaz de edición de JavaScript lista para usar. Con tecnología de un servicio de lenguaje basado en TypeScript, Visual Studio proporciona IntelliSense con más funcionalidades, compatibilidad con características modernas de JavaScript y características de productividad mejoradas, como Ir a definición, la refactorización y mucho más.

> [!NOTE]
> JavaScript Language Service en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] usa un nuevo motor para el servicio de lenguaje (denominado "Salsa"). Este tema incluye información, pero es posible que también quiera leer esta [entrada de blog](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/more-productive-javascript-in-visual-studio-2017-rc/). La nueva experiencia de edición también se centra principalmente en el código de Visual Studio. Consulte [documentos de VS Code](https://code.visualstudio.com/docs/languages/javascript) para obtener más información.

Para más información sobre la funcionalidad general de IntelliSense de Visual Studio, vea [Usar IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Novedades de JavaScript Language Service en [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Desde [!include[vs_dev15](../misc/includes/vs_dev15_md.md)], JavaScript IntelliSense muestra mucha más información sobre las listas de parámetros y miembros.
Esta nueva información la proporciona el servicio de lenguaje TypeScript, que usa el análisis estático en segundo plano para comprender mejor el código.
TypeScript usa varios orígenes para generar esta información:

- [IntelliSense basado en la inferencia de tipos](#TypeInference)
- [IntelliSense basado en JSDoc](#JsDoc)
- [IntelliSense basado en archivos de declaración de TypeScript](#TsDeclFiles)
- [Adquisición automática de definiciones de tipo](#Auto)

<a name="TypeInference"></a>
### <a name="intellisense-based-on-type-inference"></a>IntelliSense basado en la inferencia de tipos

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

En el caso de parámetros de función, actualmente no hay ninguna inferencia, pero hay formas de solucionar este problema mediante archivos *.d.ts* de JSDoc o TypeScript (vea las secciones posteriores).

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

<a name="JsDoc"></a>
### <a name="intellisense-based-on-jsdoc"></a>IntelliSense basado en JSDoc

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

Vea [JSDoc support in JavaScript](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) (Compatibilidad de JSDoc en JavaScript) para conocer las anotaciones de JsDoc compatibles en este momento.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>IntelliSense basado en archivos de declaración de TypeScript

Dado que TypeScript y JavaScript se basan ahora en el mismo servicio de lenguaje, pueden interactuar de manera más completa. Por ejemplo, se puede proporcionar IntelliSense para JavaScript para valores declarados en un archivo *.d.ts* (vea la [documentación de TypeScript](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), y los tipos como interfaces y clases declarados en TypeScript están disponibles para su uso como tipos en comentarios de JsDoc.

A continuación, se muestra un ejemplo sencillo de un archivo de definición de TypeScript que proporciona esa información de tipo (a través de una interfaz) a un archivo JavaScript del mismo proyecto (con una etiqueta de `JsDoc`).

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640" alt="TypeScript definition file" />

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Adquisición automática de definiciones de tipo

En el mundo de TypeScript, las bibliotecas más populares de JavaScript tienen sus API descritas mediante archivos *.d.ts* y el repositorio más común para esas definiciones se encuentra en [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

De manera predeterminada, el servicio de lenguaje Salsa intenta detectar qué bibliotecas de JavaScript están en uso. Además, descarga y hace referencia de forma automática al archivo *.d.ts* correspondiente que describe la biblioteca para proporcionar IntelliSense con más funcionalidades. Los archivos se descargan en una caché ubicada en la carpeta de usuario en *%LOCALAPPDATA%\Microsoft\TypeScript*.

> [!NOTE]
> Esta característica está **deshabilitada** de forma predeterminada si se usa un archivo de configuración *tsconfig.json*, pero se puede habilitar, como se describe más adelante.

Actualmente, la detección automática funciona para las dependencias descargadas desde npm (al leer el archivo *package.json*), Bower (al leer el archivo *bower.json*) y para archivos separados del proyecto que coinciden con una lista de aproximadamente las 400 bibliotecas de JavaScript más populares. Por ejemplo, si tiene *jquery-1.10.min.js* en el proyecto, el archivo *jquery.d.ts* se captura y carga para proporcionar una mejor experiencia de edición. Este archivo *.d.ts* no tiene ningún impacto en el proyecto.

Si no quiere usar la adquisición automática, puede deshabilitarla mediante la adición de un archivo de configuración como se describe a continuación. Aún puede colocar archivos de definición de forma manual para usarlos directamente en el proyecto.

## <a name="see-also"></a>Vea también

- [Usar IntelliSense](../ide/using-intellisense.md)
- [Compatibilidad con JavaScript (Visual Studio para Mac)](/visualstudio/mac/javascript)