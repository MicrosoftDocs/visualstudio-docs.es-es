---
title: "Extracción de una interfaz en Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 98a3a96357eb6e7391eb92bd0ac3a53dd00f09f5
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="extract-an-interface-in-visual-basic"></a>Extracción de una interfaz en Visual Basic

**Qué:** Le permite crear una interfaz con los miembros existentes de una clase, estructura o interfaz.

**Cuándo:** Tiene varias clases, estructuras o interfaces con métodos que podrían hacerse comunes y utilizarse por otras clases, estructuras o interfaces.

**Por qué:** Las interfaces son excelentes construcciones para diseños orientados a objetos.  Imagine que tiene clases para varios animales (Perro, Gato, Pájaro) que podrían tener métodos en común, como Comer, Beber, Dormir.  Usando una interfaz como IAnimal, podría hacer que Perro, Gato y Pájaro tengan una "firma" común para estos métodos.  

**Cómo**:

1. Resalte el nombre de la clase en la que va a realizar la acción, o simplemente coloque el cursor de texto en alguna parte del nombre de la clase.

   ![Código resaltado](media/extractinterface-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **CTRL+R** y, a continuación, **CTRL+I**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Extraer interfaz** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Seleccione **Editar > Refactorizar > Extraer interfaz**.
     * Haga clic con el botón derecho en el nombre de la clase, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Extraer interfaz** en el menú emergente de la ventana Vista previa.

1. En el cuadro de diálogo **Extraer interfaz** que aparece, escriba la información que se le solicita: ![Extraer interfaz](media/extractinterface-dialog-vb.png)
   | Campo | Description |
   | --- | --- |
   | **Nuevo nombre de interfaz** | Nombre de la interfaz que se va a crear. El valor predeterminado es I*ClassName*, donde *ClassName* es el nombre de la clase seleccionada anteriormente. |
   | **Nuevo nombre de archivo** | El nombre del archivo que se generará y que contendrá la interfaz. Al igual que con el nombre de la interfaz, el valor predeterminado es I*ClassName*, donde *ClassName* es el nombre de la clase seleccionada anteriormente. |
   | **Seleccionar miembros públicos para formar interfaz** | Los elementos que se van a extraer a la interfaz.  Puede seleccionar tantos como desee. |

1. Haga clic en **Aceptar**.

   La interfaz se creará inmediatamente en el archivo del nombre especificado.  Además, la clase seleccionada ahora implementará esa interfaz.

   ![Clase resultante](media/extractinterface-class-vb.png)
   ![Interfaz resultante](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)