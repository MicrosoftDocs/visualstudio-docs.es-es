---
title: "Traslado de un tipo a un archivo coincidente: refactorización (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 510b984ad2de9476d53e9a5a4bcd667f393d3d4b
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="move-type-to-a-matching-file-in-visual-basic"></a>Traslado de un tipo a un archivo coincidente en Visual Basic

**Qué:** Le permite mover el tipo seleccionado a un archivo independiente con el mismo nombre.

**Cuándo:** Tiene varias clases, estructuras, interfaces, etc. en el mismo archivo que desea separar.  

**Por qué:** Colocar varios tipos en el mismo archivo puede dificultar su búsqueda.  Al trasladar los tipos a archivos con el mismo nombre, es más fácil leer el código y navegar hasta él.

**Cómo**:

1. Resalte o coloque el cursor de texto en el nombre del tipo que se va a mover:

   ![Código resaltado](media/movetype-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Mover tipo a *NombreTipo*.vb** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.
   * **Mouse**
     * Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Mover tipo a *NombreTipo*.vb** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.

   El tipo se moverá al instante en un archivo nuevo con ese nombre dentro de la solución.

   ![Resultado en línea](media/movetype-result-vb.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)