---
title: "Generar un campo, propiedad o local: generación de código (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 85d15d28fae994f029e678183d2f08d561c70f1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-field-property-or-local-in-c"></a>Generar un campo, propiedad o valor local en C# #
**¿Qué:** le permite generar inmediatamente el código para un campo no declarado previamente, propiedad o local. 

**Cuándo:** introducir un nuevo campo, propiedad o valor local mientras se escribe y desea correctamente, declare automáticamente.  

**Por este motivo:** podría declarar el campo, propiedad o valor local antes de usarlo, sin embargo, esta característica generará la declaración y escriba automáticamente. 

**Cómo:**

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha usado un campo, de forma local o una propiedad que aún no existe.

   ![Código que aparece resaltado](media/field_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Generar campo o propiedad/local** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **Generar campo o propiedad/local** desde la ventana emergente de ventana de vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el ![Bombilla](media/bulb.png) icono que aparece.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la línea roja ondulada.

   ![Generar vista previa de campo o propiedad/local](media/field_preview.png)

   >[!TIP]
   >Use la [ **obtener una vista previa de cambios** ](../../ide/preview-changes.md) vínculo en la parte inferior de la ventana de vista previa para ver todos los cambios que se realizarán antes de realizar la selección.

1. El campo, propiedad o valor local, se creará automáticamente con el tipo deducido de su uso.

   ![Generar resultados de campo o propiedad/local](media/field_result.png)

## <a name="see-also"></a>Vea también  
[Code Generation (C#)](../code-generation-csharp.md) (Generación de código (C#))  
[Vista previa de cambios](../../ide/preview-changes.md) 
