---
title: Especificar eventos de compilación personalizados en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68068a88744484e0f9d1849a430a32fd3f4c1899
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Especificar eventos de compilación personalizados en Visual Studio
Mediante la especificación de un evento de compilación personalizado, puede ejecutar automáticamente comandos antes de que iniciar o finalizar una compilación. Por ejemplo, puede ejecutar un archivo .bat antes de que iniciar una compilación o copiar archivos nuevos en una carpeta una vez finalizada esta. Los eventos de compilación se ejecutan solo si se alcanzan correctamente esos puntos en el proceso de compilación.  
  
 Para obtener información específica sobre el lenguaje de programación que está usando, vea los temas siguientes:  
  
-   Visual Basic: [Cómo: Especificar eventos de compilación (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).  
  
-   C# y F#: [Cómo: Especificar eventos de compilación (C#)](../ide/how-to-specify-build-events-csharp.md).  
  
-   Visual C++: [Especificar eventos de compilación](/cpp/ide/specifying-build-events).  
  
## <a name="syntax"></a>Sintaxis  
 Los eventos de compilación siguen la misma sintaxis que los comandos de DOS, pero puede usar macros para crear eventos más fácilmente. Para obtener una lista de las macros disponibles, vea [Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
 Para obtener mejores resultados, siga estas sugerencias de formato:  
  
-   Agregue una instrucción `call` antes de todos los eventos de compilación que ejecutan archivos .bat.  
  
     Ejemplo: `call C:\MyFile.bat`  
  
     Ejemplo: `call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   Escriba las rutas de acceso entre comillas.  
  
     Ejemplo (para [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"  
  
-   Separe varios comandos mediante saltos de línea.  
  
-   Incluya caracteres comodín según sea necesario.  
  
     Ejemplo: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`  
  
    > [!NOTE]
    >  `%I` en el código anterior debe ser `%%I` en scripts por lotes.  
  
## <a name="see-also"></a>Vea también  
 [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)   
 [Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md)   
 [Tutorial: Compilar una aplicación](../ide/walkthrough-building-an-application.md)