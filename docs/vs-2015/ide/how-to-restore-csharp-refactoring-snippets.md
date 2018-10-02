---
title: 'Cómo: Restaurar miniprogramas de refactorización de C# | Microsoft Docs'
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
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13867274ace5582b25482868ddd3642426b1f295
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575253"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Cómo: Restaurar miniprogramas de refactorización de C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: restaurar los fragmentos de refactorización C#](https://docs.microsoft.com/visualstudio/ide/how-to-restore-csharp-refactoring-snippets).  
  
Las operaciones de refactorización de C# dependen de fragmentos de código situados en el directorio siguiente:  
  
 *Directorio de instalación*\Microsoft Visual Studio 14.0\VC#\Snippets\\*Id. de idioma*\Refactoring  
  
 Si este directorio Refactoring o cualquiera de sus archivos se elimina o se daña, es posible que las operaciones de refactorización de C# no funcionen en el IDE.  Los procedimientos siguientes pueden ayudarle a restaurar los fragmentos de código de refactorización de C#.  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Para comprobar que los miniprogramas de refactorización de C# están disponibles a través del Administrador de fragmentos de código  
  
1.  En el menú **Herramientas**, seleccione **Code Snippet Manager** (Administrador de fragmentos de código).  
  
2.  En el cuadro de diálogo **Code Snippet Manager** (Administrador de fragmentos de código), seleccione **Visual C#** en la lista desplegable **Lenguaje**.  
  
     Debería aparecer una carpeta **Refactorización** en la lista de carpetas de la vista de árbol.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Para restaurar la refactorización, consulte el comentario en el Administrador de fragmentos de código  
  
1.  Si la carpeta **Refactorización** no aparece en la lista de carpetas de la vista de árbol del Administrador de fragmentos de código, use este procedimiento para volver a agregar los fragmentos de refactorización en el Administrador de fragmentos de código.  
  
2.  En el menú **Herramientas**, seleccione **Code Snippet Manager** (Administrador de fragmentos de código).  
  
3.  En el cuadro de diálogo **Code Snippet Manager** (Administrador de fragmentos de código), seleccione **Visual C#** en la lista desplegable **Lenguaje**.  
  
4.  Haga clic en **Agregar**. Aparece el cuadro de diálogo **Directorio de fragmentos de código**, que le permite buscar y especificar el directorio para volver a agregar en el Administrador de fragmentos de código.  
  
5.  Busque la carpeta **Refactorización**, cuya ruta de acceso del directorio es la siguiente:  
  
     *Directorio de instalación*\Microsoft Visual Studio 14.0\VC#\Snippets\\*Id. de idioma*\Refactoring  
  
     La ruta de acceso real es similar a la siguiente para una instalación predeterminada:  
  
     C:\Archivos de programa\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring.  
  
6.  Haga clic en **Abrir** en el cuadro de diálogo **Directorio de fragmentos de código** y, después, haga clic en **Aceptar** en el Administrador de fragmentos de código.  
  
## <a name="see-also"></a>Vea también  
 [Fragmentos de código de Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Refactorización (C#)](../csharp-ide/refactoring-csharp.md)   
 [Fragmentos de código](../ide/code-snippets.md)



