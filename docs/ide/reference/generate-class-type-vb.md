---
title: "Generación de una clase o tipo: generación de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vsl.GenerateFromUsage
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4a4ff45a59fb53964a365f31cc4d5f48a5b159dc
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-class-or-type-in-visual-basic"></a>Generación de una clase o tipo en Visual Basic
**Qué:** Le permite generar el código de inmediato para una clase o un tipo. 

**Cuándo:** Introduce una nueva clase o un tipo y desea declararlo de manera adecuada y de inmediato.  

**Por qué:** Podría declarar la clase o el tipo antes de usarlo; sin embargo, esta característica generará la clase o el tipo automáticamente. 

**Cómo**:

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha utilizado una clase que aún no existe.

   ![Código resaltado](media/class-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione una de las opciones en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija una de las opciones en el menú emergente de la ventana Vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-vb.png) que aparece.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-vb.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

   ![Vista previa de generación de clase](media/class-preview-vb.png)

   Selección | Description
   --- | ---
   Generar clase "*NombreTipo*" en el nuevo archivo | Crea una clase denominada *NombreTipo* en un archivo denominado *NombreTipo*.cs/.vb
   Generar clase "*NombreTipo*" | Crea una clase denominada *NombreTipo* en el archivo actual.
   Generar clase anidada "*NombreTipo*" | Crea una clase denominada *NombreTipo* anidada en la clase actual.
   Generar nuevo tipo... | Crea una nueva clase o estructura con todas las propiedades que especifique.

   >[!TIP]
   >Use el vínculo [**Vista previa de los cambios**](../../ide/preview-changes.md) en la parte inferior de la ventana de vista previa para ver todos los cambios que se aplicarán antes de hacer la selección.

1. Si selecciona el elemento **Generar nuevo tipo...**, aparecerá un cuadro de diálogo que le permite realizar algunas acciones adicionales.

   ![Generar tipo](media/class-newtype-vb.png)

   Selección | Description
   --- | ---
   Access | Configure el tipo para que tenga acceso *Predeterminado*, *Interno* o *Público*.
   Tipo | Esta propiedad puede establecerse como *clase* o *struct*.
   nombre | No se puede cambiar y será el nombre que ya ha escrito.
   Proyecto | Si hay varios proyectos en la solución, puede elegir dónde desea que resida la clase/estructura.
   Nombre de archivo | Puede crear un nuevo archivo o agregar el tipo a un archivo existente.

1. La clase/estructura se creará automáticamente con el constructor que se deduce de su uso.

   ![Generar resultado de clase](media/class-result-vb.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)