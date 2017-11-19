---
title: "Mover el tipo de archivo coincidente - refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f58c34-c50f-4297-91b2-2e243380dcc9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9fa5a15f9c8e688c973594309efbfa6cb5d10e8b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="move-a-type-to-a-matching-file-in-c"></a>Mover un tipo a un archivo coincidente en C# #
**¿Qué:** le permite mover el tipo seleccionado a un archivo independiente con el mismo nombre.

**Cuándo:** tienen varias clases, structs, interfaces, etc. en el mismo archivo que desea separar.  

**Por este motivo:** colocar varios tipos en el mismo archivo puede dificultar a encontrar estos tipos.  Moviendo los tipos a los archivos con el mismo nombre, código pasa a ser más legible y más fácil navegar.

**Cómo:**

1. Resalte o coloque el cursor de texto en el nombre del tipo para mover:

   ![Código que aparece resaltado](media/movetype_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Mover tipo a *TypeName*.cs** desde la ventana emergente la ventana de vista previa, donde *TypeName* es el nombre del tipo que ha seleccionado.
   * **Mouse**
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **Mover tipo a *TypeName*.cs** desde la ventana emergente la ventana de vista previa, donde  *TypeName* es el nombre del tipo que ha seleccionado.

   El tipo va a mover al instante en un archivo nuevo con ese nombre dentro de la solución.

   ![Resultados inline](media/movetype_result.png)

## <a name="see-also"></a>Vea también  
[Refactorización (C#)](../refactoring-csharp.md)