---
title: "Generar un campo, propiedad o local: generación de código (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2dd0ef0db74a0ee723c7cd09bd8118e646b8ba3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>Generar un campo, propiedad o valor local en Visual Basic
**¿Qué:** le permite generar inmediatamente el código para un campo no declarado previamente, propiedad o local. 

**Cuándo:** introducir un nuevo campo, propiedad o valor local mientras se escribe y desea correctamente, declare automáticamente.  

**Por este motivo:** podría declarar el campo, propiedad o valor local antes de usarlo, sin embargo, esta característica generará la declaración y escriba automáticamente. 

**Cómo:**

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha usado un campo, de forma local o una propiedad que aún no existe.

   ![Código que aparece resaltado](media/field_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione  **generar variable '*nombre*' > Generar propiedad/campo/local ** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione  **generar variable '*nombre*' > Generar propiedad/campo/local ** desde la vista previa menú emergente de la ventana.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el ![Bombilla](media/bulb.png) icono que aparece.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la línea roja ondulada.

   ![Generar vista previa de campo o propiedad/local](media/field_preview.png)

   >[!TIP]
   >Use la [ **obtener una vista previa de cambios** ](../../ide/preview-changes.md) vínculo en la parte inferior de la ventana de vista previa para ver todos los cambios que se realizarán antes de realizar la selección.

1. El campo, propiedad o valor local, se creará automáticamente con el tipo deducido de su uso.

   ![Generar resultados de campo o propiedad/local](media/field_result.png)

## <a name="see-also"></a>Vea también  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generación de código (Visual Basic))  
[Vista previa de cambios](../../ide/preview-changes.md)