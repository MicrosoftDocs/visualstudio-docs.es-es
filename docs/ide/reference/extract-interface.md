---
title: Refactorización de extracción de una interfaz en Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b126d3753c0b4d92a3ef7bc2579c6208e61e308b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849889"
---
# <a name="extract-an-interface-refactoring"></a>Refactorización de extracción de una interfaz

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite crear una interfaz con los miembros existentes de una clase, estructura o interfaz.

**Cuándo:** Tiene varias clases, estructuras o interfaces con métodos que podrían hacerse comunes y utilizarse por otras clases, estructuras o interfaces.

**Por qué:** Las interfaces son excelentes construcciones para diseños orientados a objetos. Imagine que tiene clases para varios animales (Perro, Gato, Pájaro) que podrían tener métodos en común, como Comer, Beber, Dormir. Usando una interfaz como IAnimal, podría hacer que Perro, Gato y Pájaro tengan una "firma" común para estos métodos.

## <a name="how-to"></a>Procedimiento

1. Resalte el nombre de la clase en la que va a realizar la acción, o simplemente coloque el cursor de texto en alguna parte del nombre de la clase.

   - C#:

       ![Código resaltado (C#)](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (Visual Basic)](media/extractinterface-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **CTRL+R** y, a continuación, **CTRL+I**. (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Extraer interfaz** en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Seleccione **Editar > Refactorizar > Extraer interfaz**.
      - Haga clic con el botón derecho en el nombre de la clase, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Extraer interfaz** en el menú emergente de la ventana Vista previa.

3. En el cuadro de diálogo **Extraer interfaz** que se abre, escriba la información que se le pide:

   ![Extraer interfaz](media/extractinterface-dialog-cs.png)


   | Campo | Descripción |
   | - | - |
   | **Nuevo nombre de interfaz** | Nombre de la interfaz que se va a crear. El valor predeterminado es I*ClassName*, donde *ClassName* es el nombre de la clase seleccionada anteriormente. |
   | **Nuevo nombre de archivo** | El nombre del archivo que se generará y que contendrá la interfaz. Al igual que con el nombre de la interfaz, el valor predeterminado es I*ClassName*, donde *ClassName* es el nombre de la clase seleccionada anteriormente. |
   | **Seleccionar miembros públicos para formar interfaz** | Los elementos que se van a extraer a la interfaz. Puede seleccionar tantos como desee. |


4. Elija **Aceptar**.

   La interfaz se crea en el archivo del nombre especificado. Además, la clase seleccionada ahora implementa esa interfaz.

   - C#:

      ![Clase resultante (C#)](media/extractinterface-class-cs.png) ![Interfaz resultante (C#)](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Clase resultante (Visual Basic)](media/extractinterface-class-vb.png) ![Interfaz resultante (Visual Basic)](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)