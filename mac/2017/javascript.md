---
title: JavaScript y TypeScript
description: Información sobre la compatibilidad con Javascript en Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 5f1a400506f7766ba22ffbc1debde687b1709a21
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760931"
---
# <a name="javascript-and-typescript-support"></a>Compatibilidad con JavaScript y TypeScript

Visual Studio para Mac proporciona compatibilidad con Javascript y TypeScript mediante el resaltado de sintaxis, el formato de código e IntelliSense.

![compatibilidad del editor de TypeScript](/visualstudio/mac/media/tsjseditor-2019.gif)

Para obtener más información sobre la escritura de JavaScript, consulte las guías [Escribir código JavaScript](/scripting/javascript/writing-javascript-code).

## <a name="adding-a-javascript-file"></a>Agregar un archivo JavaScript

Los archivos JavaScript se suelen agregar a los proyectos de ASP.NET Core mediante el cuadro de diálogo **Nuevo archivo**. Para agregar un archivo JavaScript, haga doble clic en el proyecto y vaya a **Agregar > Nuevo archivo**:

![agregar archivos nuevos al proyecto](media/javascript-image1.png)

En el cuadro de diálogo **Nuevo archivo**, seleccione **Web > Archivo JS vacío** o **Web > Archivo TypeScript**. Asígnele un nombre y elija **Aceptar**:

![crear un nuevo archivo TypeScript desde la plantilla](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio para Mac usa [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) para proporcionar IntelliSense, lo que permite finalizar el código de forma inteligente y obtener información de parámetros y listas de miembros al escribir código.

Javascript IntelliSense en Visual Studio para Mac puede basarse en la inferencia de tipos, JSDoc o declaración de TypeScript.

- **Inferencia de tipos**: el tipo de un objeto se determina por el contexto del código que lo rodea. Para obtener más información, vea la sección de Visual Studio [IntelliSense basado en la inferencia de tipos](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc**: hay ocasiones en que la inferencia de tipos no proporciona la información de tipo correcta. En estos casos, la información de tipo puede proporcionarse explícitamente por anotaciones [JSDoc](https://jsdoc.app/about-getting-started.html). Para obtener más información, vea la sección de Visual Studio [IntelliSense basado en JSDoc](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc).
- **Archivos de declaración de TypeScript**: los archivos `.d.ts` se usan para proporcionar los valores para Javascript IntelliSense. Los tipos declarados en ese archivo se pueden usar como tipos en los comentarios de JSDoc. Para obtener más información, vea la sección de Visual Studio de [IntelliSense basado en archivos de declaración de TypeScript](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)

    ![sobre cómo agregar un archivo de definición de TypeScript](media/javascript-image3.png)

## <a name="see-also"></a>Consulte también

- [IntelliSense para JavaScript (Visual Studio en Windows)](/visualstudio/ide/javascript-intellisense)
