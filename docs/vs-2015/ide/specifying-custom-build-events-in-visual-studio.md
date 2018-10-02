---
title: Especificar eventos de compilación personalizados en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3ef870cb6973ff35d620ff09ac781686a9dca508
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581747"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Especificar eventos de compilación personalizados en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [especificar crear eventos personalizados en Visual Studio](https://docs.microsoft.com/visualstudio/ide/specifying-custom-build-events-in-visual-studio).  
  
Mediante la especificación de un evento de compilación personalizado, puede ejecutar automáticamente comandos antes de que iniciar o finalizar una compilación. Por ejemplo, puede ejecutar un archivo .bat antes de que iniciar una compilación o copiar archivos nuevos en una carpeta una vez finalizada esta. Los eventos de compilación se ejecutan solo si se alcanzan correctamente esos puntos en el proceso de compilación.  
  
 Para obtener información específica acerca del lenguaje de programación que está usando, consulte los temas siguientes:  
  
-   Visual Basic: [Cómo: Especificar eventos de compilación (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).  
  
-   Visual C# y F#: [Cómo: Especificar eventos de compilación (C#)](../ide/how-to-specify-build-events-csharp.md).  
  
-   Visual C++: [Especificar eventos de compilación](http://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc).  
  
## <a name="syntax"></a>Sintaxis  
 Los eventos de compilación siguen la misma sintaxis que los comandos de DOS, pero puede usar macros para crear eventos más fácilmente. Para obtener una lista de las macros disponibles, vea [Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
 Para obtener mejores resultados, siga estas sugerencias de formato:  
  
-   Agregue una instrucción `call` antes de todos los eventos de compilación que ejecutan archivos .bat.  
  
     Ejemplo: `call C:\MyFile.bat`  
  
     Ejemplo: `call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   Escriba las rutas de acceso entre comillas.  
  
     Ejemplo (para [!INCLUDE[win8](../includes/win8-md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"  
  
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



