---
title: Refactorización de traslado de un tipo a un archivo coincidente en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4cabe20e6cf84b69bf711831d1a402f67fd908c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Refactorización de traslado de un tipo a un archivo coincidente

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite mover el tipo seleccionado a un archivo independiente con el mismo nombre.

**Cuándo:** Tiene varias clases, estructuras, interfaces, etc. en el mismo archivo que desea separar.

**Por qué:** Colocar varios tipos en el mismo archivo puede dificultar su búsqueda. Al trasladar los tipos a archivos con el mismo nombre, es más fácil leer el código y navegar hasta él.

## <a name="how-to"></a>Procedimiento

1. Resalte o coloque el cursor de texto en el nombre del tipo que se va a mover:

   - C#:

    ![Código resaltado (C#)](media/movetype-highlight-cs.png)

   - Visual Basic:

    ![Código resaltado (Visual Basic)](media/movetype-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
     - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Mover tipo a *NombreTipo*.cs** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.
   - **Mouse**
     - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Mover tipo a *NombreTipo*.cs** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.

   El tipo se traslada a un nuevo archivo con ese nombre como parte de la solución.

   - C#:

    ![Resultado de la inserción (C#)](media/movetype-result-cs.png)

   - Visual Basic:

    ![Resultado de la inserción (Visual Basic)](media/movetype-result-vb.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)