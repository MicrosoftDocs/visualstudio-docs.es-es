---
title: "Generación de una clase o tipo: generación de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 87ef385a7e9edf9f975eb579bfab292039d60fa2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-class-or-type-in-c"></a>Generación de una clase o tipo en C# #
**Qué:** Le permite generar el código de inmediato para una clase o un tipo. 

**Cuándo:** Introduce una nueva clase o un tipo y desea declararlo de manera adecuada y de inmediato.  

**Por qué:** Podría declarar la clase o el tipo antes de usarlo; sin embargo, esta característica generará la clase o el tipo automáticamente. 

**Cómo**:

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha utilizado una clase que aún no existe.

   ![Código resaltado](media/class-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione una de las opciones en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija una de las opciones en el menú emergente de la ventana Vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

   ![Vista previa de generación de clase](media/class-preview-cs.png)

   Selección | Description
   --- | ---
   Generar clase "*NombreTipo*" en el nuevo archivo | Crea una clase denominada *NombreTipo* en un archivo denominado *NombreTipo*.cs/.vb
   Generar clase "*NombreTipo*" | Crea una clase denominada *NombreTipo* en el archivo actual.
   Generar clase anidada "*NombreTipo*" | Crea una clase denominada *NombreTipo* anidada en la clase actual.
   Generar nuevo tipo... | Crea una nueva clase o estructura con todas las propiedades que especifique.

   >[!TIP]
   >Use el vínculo [**Vista previa de los cambios**](../../ide/preview-changes.md) en la parte inferior de la ventana de vista previa para ver todos los cambios que se aplicarán antes de hacer la selección.

1. Si selecciona el elemento **Generar nuevo tipo...**, aparecerá un cuadro de diálogo que le permite realizar algunas acciones adicionales.

   ![Generar tipo](media/class-newtype-cs.png)

   Selección | Description
   --- | ---
   Access | Configure el tipo para que tenga acceso *Predeterminado*, *Interno* o *Público*.
   Tipo | Esta propiedad puede establecerse como *clase* o *struct*.
   nombre | No se puede cambiar y será el nombre que ya ha escrito.
   Proyecto | Si hay varios proyectos en la solución, puede elegir dónde desea que resida la clase/estructura.
   Nombre de archivo | Puede crear un nuevo archivo o agregar el tipo a un archivo existente.

1. La clase/estructura se creará automáticamente con el constructor que se deduce de su uso.

   ![Generar resultado de clase](media/class-result-cs.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)