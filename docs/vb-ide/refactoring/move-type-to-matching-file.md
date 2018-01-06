---
title: "Mover el tipo de archivo coincidente - refactorización (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8e0b3fd-d1d9-4e3f-b0f6-9f8ffbbc6297
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 862c144c2319f6247a9fd38d7f71036a4ba090a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="move-type-to-a-matching-file-in-visual-basic"></a>Tipo de movimiento a un archivo de búsqueda de coincidencias en Visual Basic
**¿Qué:** le permite mover el tipo seleccionado a un archivo independiente con el mismo nombre.

**Cuándo:** tienen varias clases, structs, interfaces, etc. en el mismo archivo que desea separar.  

**Por este motivo:** colocar varios tipos en el mismo archivo puede dificultar a encontrar estos tipos.  Moviendo los tipos a los archivos con el mismo nombre, código pasa a ser más legible y más fácil navegar.

**Cómo:**

1. Resalte o coloque el cursor de texto en el nombre del tipo para mover:

   ![Código que aparece resaltado](media/movetype_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Mover tipo a *TypeName*.vb** desde la ventana emergente la ventana de vista previa, donde *TypeName* es el nombre del tipo que ha seleccionado.
   * **Mouse**
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **Mover tipo a *TypeName*.vb** desde la ventana emergente la ventana de vista previa, donde  *TypeName* es el nombre del tipo que ha seleccionado.

   El tipo va a mover al instante en un archivo nuevo con ese nombre dentro de la solución.

   ![Resultados inline](media/movetype_result.png)

## <a name="see-also"></a>Vea también
[Refactorización (Visual Basic)](../refactoring-vb.md)