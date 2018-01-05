---
title: "Implementar una interfaz: generación de código (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e0b8df77e82ada8197b89fcdf451e4234a43669f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="implement-an-interface-in-c"></a>Implementar una interfaz en C# #
**¿Qué:** permite generar inmediatamente el código necesario para implementar una interfaz. 

**Cuándo:** desea heredar de una interfaz.  

**Por este motivo:** manualmente podría implementar toda la interfaz de uno a uno, pero esta característica generará automáticamente todas las firmas de método. 

**Cómo:**

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha hecho referencia a una interfaz pero no ha implementado todos los miembros requeridos.

   ![Código que aparece resaltado](media/interface_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Implementar interfaz (explícitamente)** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **Implementar interfaz (explícitamente)** desde la ventana emergente de ventana de vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el ![Bombilla](media/bulb.png) icono que aparece.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la línea roja ondulada.

   ![Vista previa de clase de implementación](media/interface_preview.png)

   >[!TIP]
   >Use la [ **obtener una vista previa de cambios** ](../../ide/preview-changes.md) vínculo en la parte inferior de la ventana de vista previa para ver todos los cambios que se realizarán antes de realizar la selección.
   >
   >Además, puede usar el **documento**, **proyecto**, y **solución** vínculos en la parte inferior de la ventana de vista previa para crear las firmas de método apropiado entre varios clases que implementan la interfaz.

1. Firmas de métodos de la interfaz estará listo para implementarse, creado automáticamente.

   ![Resultado de la clase de implementación](media/interface_result.png)

   >[!TIP]
   >Use la **Implementar interfaz explícitamente** delante de cada uno de ellos genera método con el nombre de la interfaz para evitar conflictos de nombres.
   >
   >![Implementar interfaz explícitamente como resultado](media/interface_explicitresult.png); 

## <a name="see-also"></a>Vea también  
[Code Generation (C#)](../code-generation-csharp.md) (Generación de código (C#))  
[Vista previa de cambios](../../ide/preview-changes.md)  
