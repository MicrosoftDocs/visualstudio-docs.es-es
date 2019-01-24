---
title: Escribir código de JavaScript en Visual Studio sin una solución o un proyecto
titleSuffix: ''
description: Visual Studio admite la creación de código sin una dependencia en un archivo de proyecto o de solución
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e8c42bd40528dfe8567219bdc2bc4a8d216e7c6b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899761"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Desarrollar código de JavaScript y TypeScript en Visual Studio sin proyectos ni soluciones

Visual Studio 2017 incluye la capacidad de [desarrollar código sin proyectos ni soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), lo que permite abrir una carpeta de código y empezar a trabajar de inmediato con compatibilidad de editor enriquecido, como IntelliSense, búsqueda, refactorización, depuración, etc.
Además de estas características, Herramientas de Node.js para Visual Studio permite compilar archivos de TypeScript, administrar paquetes de npm y ejecutar scripts de npm.

Para empezar, seleccione **Abrir carpeta** en la página de inicio que aparece cuando se abre Visual Studio, o bien, puede seleccionar **Archivo** > **Abrir** > **Carpeta** en la barra de herramientas. El Explorador de soluciones muestra todos los archivos de la carpeta; puede abrir cualquiera de ellos para comenzar a editar. En segundo plano, Visual Studio indexa los archivos para habilitar las características de npm, compilación y depuración.

> [!IMPORTANT]
> Muchas de las características descritas en este artículo, incluida la integración con npm, requieren Visual Studio 2017 versión 15.8.

## <a name="npm-integration"></a>Integración con npm

Si la carpeta que abre contiene un archivo *package.json*, puede hacer clic con el botón derecho en *package.json* para mostrar un menú contextual (menú emergente) específico de npm. 

![Menú de npm en el Explorador de soluciones](../javascript/media/solution-explorer-npm-ctx.png) 

En el menú contextual, puede administrar los paquetes instalados por npm de la misma forma que [administra paquetes de npm](npm-package-management.md) cuando usa un archivo de proyecto.

Además, el menú también permite ejecutar los scripts definidos en el elemento `scripts` de *package.json*. Estos scripts usan la versión de Node.js disponible en la variable de entorno `PATH`. Los scripts se ejecutan en una ventana nueva. Es una excelente manera de ejecutar la compilación o scripts.

## <a name="build-and-debug"></a>Compilación y depuración

### <a name="packagejson"></a>package.json
Si el archivo *package.json* de la carpeta especifica un elemento `main`, el comando **Depurar** estará disponible en el menú contextual de *package.json*. Al hacer clic en él se inicia *node.exe* con el script especificado como argumento.

### <a name="javascript-files"></a>Archivos de JavaScript
Puede depurar archivos de JavaScript si hace clic con el botón derecho en un archivo y selecciona **Depurar** en el menú contextual. Esto inicia *node.exe* con ese archivo de JavaScript como argumento.

### <a name="typescript-files-and-tsconfigjson"></a>Archivos de TypeScript y tsconfig.json
Si no hay ningún archivo *tsconfig.json* en la carpeta, haga clic con el botón derecho en un archivo de TypeScript para ver los comandos del menú contextual para compilar y depurar ese archivo. Al usar estos comandos, se compila o se depura con *tsc.exe* con las opciones predeterminadas. (Para depurar, es necesario compilar el archivo).

> [!NOTE]
> Al compilar código de TypeScript, se usa la versión más reciente instalada en `C:\Program Files (x86)\Microsoft SDKs\TypeScript`.

Si hay un archivo *tsconfig.json* en la carpeta, puede hacer clic con el botón derecho en un archivo de TypeScript para ver un comando de menú para depurar ese archivo de TypeScript. La opción solo aparece si no hay ningún elemento `outFile` especificado en *tsconfig.json*. Si hay un `outFile` especificado, puede depurar ese archivo si hace clic con el botón derecho en *tsconfig.json* y selecciona la opción correcta. El archivo `tsconfig.json` también ofrece una opción de compilación para que pueda especificar las opciones del compilador.

> [!NOTE]
> Puede encontrar más información sobre *tsconfig.json* en la [página del manual de TypeScript sobre tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Pruebas unitarias
Puede habilitar la integración de pruebas unitarias en Visual Studio al especificar una raíz de prueba en su archivo *package.json*:

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

El ejecutor de pruebas enumera los paquetes instalados localmente para determinar qué marco de pruebas usar.
Si no se reconoce ninguno de los marcos admitidos, el ejecutor de pruebas tiene como valor predeterminado *ExportRunner*. Los otros marcos admitidos son:
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))

Después de abrir el Explorador de pruebas (elija **Prueba** > **Windows** > **Explorador de pruebas**), Visual Studio detecta y muestra las pruebas.

> [!NOTE]
> El ejecutor de pruebas solo enumerará los archivos JavaScript en la raíz de prueba; si la aplicación se ha escrito en TypeScript, tendrá que compilarlos primero.
