---
title: "Especificar eventos de compilaci&#243;n personalizados en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "eventos de compilación, personalizar"
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Especificar eventos de compilaci&#243;n personalizados en Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mediante la especificación de un evento de compilación personalizado, puede ejecutar automáticamente comandos antes de que iniciar o finalizar una compilación.  Por ejemplo, puede ejecutar un archivo .bat antes de que iniciar una compilación o copiar archivos nuevos en una carpeta una vez finalizada esta.  Los eventos de compilación se ejecutan solo si se alcanzan correctamente esos puntos en el proceso de compilación.  
  
 Para obtener información específica acerca del lenguaje de programación que está usando, consulte los temas siguientes:  
  
-   Visual Basic\-\-[Cómo: Especificar eventos de compilación \(Visual Basic\)](../ide/how-to-specify-build-events-visual-basic.md).  
  
-   Visual C\# y F \#\-\-[Cómo: Especificar eventos de compilación \(C\#\)](../ide/how-to-specify-build-events-csharp.md).  
  
-   Visual C\+\+\-\-[Especificar eventos de compilación](/visual-cpp/ide/specifying-build-events).  
  
## Sintaxis  
 Los eventos de compilación siguen la misma sintaxis que los comandos de DOS, pero puede usar macros para crear eventos más fácilmente.  Para obtener una lista de las macros disponibles, consulte [Línea de comandos del evento anterior\/posterior a la compilación \(Cuadro de diálogo\)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
 Para obtener mejores resultados, siga estas sugerencias de formato:  
  
-   Agregue una instrucción `call` antes de todos los eventos de compilación que ejecutan archivos .bat.  
  
     Ejemplo: `call C:\MyFile.bat`  
  
     Ejemplo: `call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   Escriba las rutas de acceso entre comillas.  
  
     Ejemplo \(para [!INCLUDE[win8](../debugger/includes/win8_md.md)]\): "%ProgramFiles\(x86\)%\\Microsoft SDKs\\Windows\\v8.0A\\Bin\\NETFX 4.0 Tools\\gacutil.exe" \-if "$\(TargetPath\)"  
  
-   Separe varios comandos mediante saltos de línea.  
  
-   Incluya caracteres comodín según sea necesario.  
  
     Ejemplo: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`  
  
    > [!NOTE]
    >  `%I` en el código anterior debe ser `%` en scripts por lotes.  
  
## Vea también  
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)   
 [Línea de comandos del evento anterior\/posterior a la compilación \(Cuadro de diálogo\)](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md)   
 [Tutorial: Compilar una aplicación](../ide/walkthrough-building-an-application.md)