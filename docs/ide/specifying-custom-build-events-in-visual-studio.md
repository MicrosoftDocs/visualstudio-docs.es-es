---
title: Especificación de eventos de compilación personalizados
description: Aprenda a ejecutar comandos de forma automática en Visual Studio antes de que se inicie una compilación o después de que termine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0728154e21893ac45fc0e17cc3d0407551dbb3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951035"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Especificar eventos de compilación personalizados en Visual Studio

Mediante la especificación de un evento de compilación personalizado, puede ejecutar automáticamente comandos antes de que iniciar o finalizar una compilación. Por ejemplo, puede ejecutar un archivo *.bat* antes de iniciar una compilación o copiar archivos nuevos en una carpeta una vez finalizada la compilación. Los eventos de compilación se ejecutan solo si se alcanzan correctamente esos puntos en el proceso de compilación.

Para obtener información específica sobre el lenguaje de programación que está usando, vea los temas siguientes:

- Visual Basic: [Cómo: Especificar eventos de compilación (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# y F#--[Cómo: Especificar eventos de compilación (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++: [Especificar eventos de compilación](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Sintaxis

Los eventos de compilación siguen la misma sintaxis que los comandos de DOS, pero puede usar macros para crear eventos más fácilmente. Para obtener una lista de las macros disponibles, vea [Pre-build Event/Post-build Event command line dialog box](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) (Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo)).

Para obtener mejores resultados, siga estas sugerencias de formato:

- Agregue una instrucción `call` delante de todos los eventos de compilación que ejecutan archivos *.bat*.

   Ejemplo: `call C:\MyFile.bat`

   Ejemplo: `call C:\MyFile.bat call C:\MyFile2.bat`

- Escriba las rutas de acceso entre comillas.

   Ejemplo (para [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"

- Separe varios comandos mediante saltos de línea.

- Incluya caracteres comodín según sea necesario.

   Ejemplo: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`

  > [!NOTE]
  > `%I` en el código anterior debe ser `%%I` en scripts por lotes.

## <a name="see-also"></a>Consulta también

- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
- [Pre-build Event/Post-build Event command line dialog box](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) (Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo))
- [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md)
- [Tutorial: Creación de una aplicación](../ide/walkthrough-building-an-application.md)
