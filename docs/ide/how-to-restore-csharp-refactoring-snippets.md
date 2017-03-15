---
redirect_url: /visualstudio/csharp-ide/refactoring-csharp
title: "C&#243;mo: Restaurar miniprogramas de refactorizaci&#243;n de C# | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "expansiones, no seguras"
  - "expansión no segura"
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# C&#243;mo: Restaurar miniprogramas de refactorizaci&#243;n de C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las operaciones de refactorización de C\# dependen de fragmentos de código situados en el directorio siguiente:  
  
 *Installation directory*\\Microsoft Visual Studio 14.0\\VC\#\\Snippets\\*language ID*\\Refactoring  
  
 Si este directorio Refactoring o cualquiera de sus archivos se elimina o se daña, es posible que las operaciones de refactorización de C\# no funcionen en el IDE.   Los procedimientos siguientes pueden ayudarle a restaurar los fragmentos de código de refactorización de C\#.  
  
### Para comprobar que los miniprogramas de refactorización de C\# están disponibles a través del Administrador de fragmentos de código  
  
1.  En el menú **Herramientas**, seleccione **Administrador de fragmentos de código**.  
  
2.  En el cuadro de diálogo **Administrador de fragmentos de código**, seleccione **Visual C\#** en la lista desplegable **Lenguaje**.  
  
     Una carpeta **Refactorización** debe aparecer en la lista de carpetas de la vista de árbol.  
  
### Para restaurar la refactorización, consulte el comentario en el Administrador de fragmentos de código  
  
1.  Si la carpeta **Refactorización** no aparece en la lista de carpetas de la vista de árbol del Administrador de fragmentos de código, use este procedimiento para volver a agregar los fragmentos de refactorización al Administrador de fragmentos de código.  
  
2.  En el menú **Herramientas**, seleccione **Administrador de fragmentos de código**.  
  
3.  En el cuadro de diálogo **Administrador de fragmentos de código**, seleccione **Visual C\#** en la lista desplegable **Lenguaje**.  
  
4.  Haga clic en **Agregar**.  Aparece el cuadro de diálogo **Directorio de fragmentos de código** que le permite buscar y especificar el directorio para volver a agregar en el Administrador de fragmentos de código.  
  
5.  Busque la carpeta **Refactoring**, cuya ruta de acceso del directorio es la siguiente:  
  
     *Installation directory*\\Microsoft Visual Studio 14.0\\VC\#\\Snippets\\*language ID*\\Refactoring  
  
     La ruta de acceso real es similar a la siguiente para una instalación predeterminada:  
  
     C:\\Archivos de programa\\Microsoft Visual Studio 14.0\\VC\#\\Snippets\\1033\\Refactoring.  
  
6.  Haga clic en la opción **Abrir** del cuadro de diálogo **Directorio de fragmentos de código** y, a continuación, haga clic en **Aceptar** en el Administrador de fragmentos de código.  
  
## Vea también  
 [Fragmentos de código de Visual C\#](../ide/visual-csharp-code-snippets.md)   
 [Refactorización \(C\#\)](../csharp-ide/refactoring-csharp.md)   
 [Fragmentos de código](../ide/code-snippets.md)