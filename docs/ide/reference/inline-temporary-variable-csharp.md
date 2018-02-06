---
title: "Sustitución de una variable temporal por su valor en C# | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 626224e8ed90196294f7b3ded245bb5272f70595
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="inline-a-temporary-variable-with-c"></a>Inserción de variable temporal en línea con C# #

**Qué:** Le permite quitar una variable temporal y reemplazarla por su valor.

**Cuándo:** El uso de la variable temporal dificulta la comprensión del código.

**Quitar:** El hecho de quitar una variable temporal puede facilitar la lectura del código.

**Cómo**:

1. Resalte o coloque el cursor de texto dentro de la variable temporal que se va a insertar en línea:

   ![Código resaltado](media/inline-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones**.
   * **Mouse**
     * Haga clic en el código y seleccione el menú **Acciones rápidas y refactorizaciones**.

1. Seleccione **Variable temporal en línea** en el menú emergente de la ventana Vista previa.

   La variable se quitará y sus usos se reemplazarán por el valor de la variable de forma inmediata.

   ![Resultado en línea](media/inline-result-cs.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)