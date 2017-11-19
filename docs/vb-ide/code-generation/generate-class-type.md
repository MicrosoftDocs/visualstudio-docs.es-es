---
title: "Generar una clase o tipo - de generación de código (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: VB
ms.openlocfilehash: 1524d2899d8c775a20943d2695065bfe36885a25
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-class-or-type-in-visual-basic"></a>Generar una clase o tipo en Visual Basic
**¿Qué:** le permite generar inmediatamente el código para una clase o tipo. 

**Cuándo:** introducir una nueva clase o tipo y desea correctamente, declare automáticamente.  

**Por este motivo:** podría declarar la clase o tipo antes de usarlo, sin embargo, esta característica se genere la clase o escriba automáticamente. 

**Cómo:**

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha usado una clase que aún no existe.

   ![Código que aparece resaltado](media/class_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione una de las opciones de la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione una de las opciones de la ventana emergente de ventana de vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el ![Bombilla](media/bulb.png) icono que aparece.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la línea roja ondulada.

   ![Generar vista previa de la clase](media/class_preview.png)

   Selección | Descripción
   --- | ---
   Generar clase*TypeName*' en el nuevo archivo | Crea una clase denominada *TypeName* en un archivo denominado *TypeName*.cs o .vb
   Generar clase*TypeName*' | Crea una clase denominada *TypeName* en el archivo actual.
   Generar clase anidada*TypeName*' | Crea una clase denominada *TypeName* anidada dentro de la clase actual.
   Generar nuevo tipo... | Crea una nueva clase o struct con todas las propiedades que especifique.

   >[!TIP]
   >Use la [ **obtener una vista previa de cambios** ](../../ide/preview-changes.md) vínculo en la parte inferior de la ventana de vista previa para ver todos los cambios que se realizarán antes de realizar la selección.

1. Si selecciona el **generar nuevo tipo...**  elemento, un cuadro de diálogo mostrará que le permite realizar algunas acciones adicionales.

   ![Genere el tipo](media/class_newtype.png)

   Selección | Descripción
   --- | ---
   Access | Establecer el tipo que tienen *predeterminado*, *interno* o *público* acceso.
   Tipo | Esta propiedad puede establecerse como *clase* o *struct*.
   Name | Esto no se puede cambiar y será el nombre que ha escrito.
   Proyecto | Si hay varios proyectos de la solución, puede elegir dónde desea que la clase/estructura permanece activa.
   Nombre de archivo | Puede crear un nuevo archivo o puede agregar el tipo a un archivo existente.

1. Se creará automáticamente la estructura de clase con el constructor inferido a partir de su uso.

   ![Generar el resultado de la clase](media/class_result.png)

## <a name="see-also"></a>Vea también  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generación de código (Visual Basic))  
[Vista previa de cambios](../../ide/preview-changes.md)