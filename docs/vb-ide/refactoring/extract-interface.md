---
title: "Extraer interfaz - refactorización (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: db857fb1-3e22-46e2-b15a-56ef9f329235
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: VB
ms.openlocfilehash: 9616cae1282b992722f75eee091e2c9d271e85f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="extract-an-interface-in-visual-basic"></a>Extraer una interfaz en Visual Basic
**¿Qué:** le permite crear una interfaz con los miembros existentes de una clase, estructura o interfaz.

**Cuándo:** tiene varias clases, structs o interfaces con métodos que podrían realizarse comunes y son utilizadas por otras clases, structs o interfaces.

**Por este motivo:** Interfaces son construcciones excelentes de los diseños de orientación a objetos.  Imagine tener clases para varios animales (Dog, Cat, vista de pájaro) que pueden tener métodos comunes, como la coma, bebida, suspensión.  Mediante una interfaz como IAnimal permitiera Dog, Cat y vista de pájaro tienen una común "firma" para estos métodos.  

**Cómo:**

1. Resalte el nombre de la clase para realizar la acción en, o simplemente coloca el cursor de texto en un lugar en el nombre de clase.

   ![Código que aparece resaltado](media/extractinterface_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl + R**, a continuación, **Ctrl + I**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Extraer interfaz** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Seleccione **Editar > refactorizar > Extraer interfaz**.
     * Haga clic en el nombre de la clase, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **Extraer interfaz** desde la ventana emergente de ventana de vista previa.

1. En el **Extraer interfaz** cuadro de diálogo que aparece, escriba la información más frecuentes: ![Extraer interfaz](media/extractinterface_dialog.png)
   | Campo | Descripción |
   | --- | --- |
   | **Nuevo nombre de la interfaz** | El nombre de la interfaz que se va a crear. Este valor predeterminado será I*ClassName*, donde *ClassName* es el nombre de la clase que ha seleccionado anteriormente. |
   | **Nuevo nombre de archivo** | El nombre del archivo que se generarán que contendrá la interfaz. Como con el nombre de la interfaz predeterminada es I*ClassName*, donde *ClassName* es el nombre de la clase que ha seleccionado anteriormente. |
   | **Seleccionar a miembros públicos para formar la interfaz** | Los elementos que se va a extraer a la interfaz.  Puede seleccionar tantas como desee. |

1. Haga clic en **Aceptar**.

   La interfaz se creará inmediatamente en el archivo el nombre especificado.  Además, la clase seleccionada ahora implementará esa interfaz.

   ![Clase resultante](media/extractinterface_class.png)
   ![interfaz resultante](media/extractinterface_interface.png)

## <a name="see-also"></a>Vea también
[Refactorización (Visual Basic)](../refactoring-vb.md)