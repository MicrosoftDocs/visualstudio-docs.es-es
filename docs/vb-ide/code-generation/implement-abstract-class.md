---
title: "Implementar una clase abstracta: generación de código (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 68f60b6159cad7f751dfc47a8af116ef33a164c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="implement-an-abstract-class-in-visual-basic"></a>Implementar una clase abstracta en Visual Basic
**¿Qué:** permite generar inmediatamente el código necesario para implementar una clase abstracta. 

**Cuándo:** desea heredar de una clase abstracta.  

**Por este motivo:** manualmente podría implementar todos los miembros abstractos uno por uno, sin embargo, esta característica generará automáticamente todas las firmas de método. 

**Cómo:**

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que se hereda de una clase abstracta pero no ha implementado todos los miembros requeridos.

   ![Código que aparece resaltado](media/abstract_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **implementar clase abstracta** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **implementar clase abstracta** desde la ventana emergente de ventana de vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el ![Bombilla](media/bulb.png) icono que aparece.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la línea roja ondulada.

   ![Vista previa de clase de implementación](media/abstract_preview.png)

   >[!TIP]
   >Use la [ **obtener una vista previa de cambios** ](../../ide/preview-changes.md) vínculo en la parte inferior de la ventana de vista previa para ver todos los cambios que se realizarán antes de realizar la selección.
   >
   >Además, puede usar el **documento**, **proyecto**, y **solución** vínculos en la parte inferior de la ventana de vista previa para crear las firmas de método apropiado entre varios clases que heredan de la clase abstracta.

1. Las firmas de método abstracto estará listo para implementarse, creado automáticamente.

   ![Resultado de la clase de implementación](media/abstract_result.png)

## <a name="see-also"></a>Vea también  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generación de código (Visual Basic))  
[Vista previa de cambios](../../ide/preview-changes.md)