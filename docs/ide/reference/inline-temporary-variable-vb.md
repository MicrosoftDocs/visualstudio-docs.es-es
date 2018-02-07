---
title: "Sustitución de una variable temporal por su valor en Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7553a67892322a1acb2db33d7a16b399b6f0b23a
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2018
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>Inserción de variable temporal en línea en Visual Basic

**Qué:** Le permite quitar una variable temporal y reemplazarla por su valor.

**Cuándo:** El uso de la variable temporal dificulta la comprensión del código.

**Quitar:** El hecho de quitar una variable temporal puede facilitar la lectura del código.

**Cómo**:

1. Resalte o coloque el cursor de texto dentro de la variable temporal que se va a insertar en línea:

   ![Código resaltado](media/inline-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones**.
   * **Mouse**
     * Haga clic en el código y seleccione el menú **Acciones rápidas y refactorizaciones**.

1. Seleccione **Variable temporal en línea** en el menú emergente de la ventana Vista previa.

   La variable se quitará y sus usos se reemplazarán por el valor de la variable de forma inmediata.

   ![Resultado en línea](media/inline-result-vb.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)