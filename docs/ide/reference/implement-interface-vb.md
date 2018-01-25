---
title: "Implementación de una interfaz: generación de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 990f87cd0f1abf9d4f62ecd321ef038d689b75f4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-interface-in-visual-basic"></a>Implementación de una interfaz en Visual Basic
**Qué:** Le permite generar inmediatamente el código necesario para implementar una interfaz. 

**Cuándo:** Desea heredar de una interfaz.  

**Por qué:** Podría implementar manualmente todas las interfaces una por una, sin embargo, esta característica generará automáticamente todas las firmas de método de manera automática. 

**Cómo**:

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha hecho referencia a una interfaz pero no ha implementado todos los miembros requeridos.

   ![Código resaltado](media/interface-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Implementar la interfaz de forma explícita** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Implementar la interfaz de forma explícita** en el menú emergente de la ventana Vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-vb.png) que aparece.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-vb.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

   ![Vista previa de la implementación de la clase](media/interface-preview-vb.png)

   >[!TIP]
   >Use el vínculo [**Vista previa de los cambios**](../../ide/preview-changes.md) en la parte inferior de la ventana de vista previa para ver todos los cambios que se aplicarán antes de hacer la selección.
   >
   >Además, puede usar los vínculos **Documento**, **Proyecto** y **Solución** de la parte inferior de la ventana de vista previa para crear las firmas de método adecuadas entre las múltiples clases que implementan la interfaz.

1. Las firmas de método de la interfaz se crearán automáticamente y estarán listas para su implementación.

   ![Resultado de la implementación de la clase](media/interface-result-vb.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)