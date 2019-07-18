---
title: 'Procedimiento: Restauración de fragmentos de código de refactorización en C# | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9f81514db881ad26a5fa827b0bde11df2467f23d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186284"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Cómo: Restaurar miniprogramas de refactorización de C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las operaciones de refactorización de C# dependen de fragmentos de código situados en el directorio siguiente:  
  
 *Directorio de instalación*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID_de_lenguaje*\Refactoring  
  
 Si este directorio Refactoring o cualquiera de sus archivos se elimina o se daña, es posible que las operaciones de refactorización de C# no funcionen en el IDE. Los procedimientos siguientes pueden ayudarle a restaurar los fragmentos de código de refactorización de C#.  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Para comprobar que los miniprogramas de refactorización de C# están disponibles a través del Administrador de fragmentos de código  
  
1. En el menú **Herramientas**, seleccione **Code Snippet Manager** (Administrador de fragmentos de código).  
  
2. En el cuadro de diálogo **Code Snippet Manager** (Administrador de fragmentos de código), seleccione **Visual C#** en la lista desplegable **Lenguaje**.  
  
     Debería aparecer una carpeta **Refactorización** en la lista de carpetas de la vista de árbol.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Para restaurar la refactorización, consulte el comentario en el Administrador de fragmentos de código  
  
1. Si la carpeta **Refactorización** no aparece en la lista de carpetas de la vista de árbol del Administrador de fragmentos de código, use este procedimiento para volver a agregar los fragmentos de refactorización en el Administrador de fragmentos de código.  
  
2. En el menú **Herramientas**, seleccione **Code Snippet Manager** (Administrador de fragmentos de código).  
  
3. En el cuadro de diálogo **Code Snippet Manager** (Administrador de fragmentos de código), seleccione **Visual C#** en la lista desplegable **Lenguaje**.  
  
4. Haga clic en **Agregar**. Aparece el cuadro de diálogo **Directorio de fragmentos de código**, que le permite buscar y especificar el directorio para volver a agregar en el Administrador de fragmentos de código.  
  
5. Busque la carpeta **Refactorización**, cuya ruta de acceso del directorio es la siguiente:  
  
     *Directorio de instalación*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID_de_lenguaje*\Refactoring  
  
     La ruta de acceso real es similar a la siguiente para una instalación predeterminada:  
  
     C:\Archivos de programa\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring.  
  
6. Haga clic en **Abrir** en el cuadro de diálogo **Directorio de fragmentos de código** y, después, haga clic en **Aceptar** en el Administrador de fragmentos de código.  
  
## <a name="see-also"></a>Otras referencias  
 [Fragmentos de código de Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)   
 [Fragmentos de código](../ide/code-snippets.md)
