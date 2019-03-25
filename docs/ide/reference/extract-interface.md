---
title: Refactorización de extracción de una interfaz
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cdead60fbde711ac9b219a6bbcb635e329d51a0a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983210"
---
# <a name="extract-an-interface-refactoring"></a>Refactorización de extracción de una interfaz

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Permite crear una interfaz con los miembros existentes de una clase, estructura o interfaz.

**Cuándo:** Tiene miembros de una clase, estructura o interfaz que otras clases, estructuras o interfaces podrían heredar.

**Por qué:** Las interfaces son excelentes construcciones para diseños orientados a objetos. Imagine que tiene clases para varios animales (Perro, Gato, Pájaro) que podrían tener métodos en común, como Comer, Beber, Dormir. Usando una interfaz como IAnimal, podría hacer que Perro, Gato y Pájaro tengan una "firma" común para estos métodos.

## <a name="extract-an-interface-refactoring"></a>Refactorización de extracción de una interfaz

1. Coloque el cursor en el nombre de clase.

   - C#:

       ![Código resaltado (C#)](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (Visual Basic)](media/extractinterface-highlight-vb.png)

2. Luego realice alguna de las siguientes acciones:

   - **Teclado**
      - Presione **CTRL+R** y, a continuación, **CTRL+I**. (El método abreviado de teclado puede variar en función del perfil que se haya seleccionado).
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Extraer interfaz** en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Seleccione **Editar > Refactorizar > Extraer interfaz**.
      - Haga clic con el botón derecho en el nombre de la clase, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Extraer interfaz** en el menú emergente de la ventana Vista previa.

3. En el cuadro de diálogo **Extraer interfaz** que se abre, escriba la información que se le pide:

   ![Extraer interfaz](media/extractinterface-dialog-same-file.png)


   | Campo | Descripción |
   | - | - |
   | **Nuevo nombre de interfaz** | Nombre de la interfaz que se va a crear. El nombre predeterminado es I*ClassName*, donde *ClassName* es el nombre de la clase seleccionada anteriormente. |
   | **Nuevo nombre de archivo** | Nombre del archivo generado que va a incluir la interfaz. Al igual que el nombre de interfaz, el nombre predeterminado es I*ClassName*, donde *ClassName* es el nombre de la clase seleccionada anteriormente. También puede seleccionar la opción **Agregar al archivo actual**. |
   | **Seleccionar miembros públicos para formar interfaz** | Los elementos que se van a extraer a la interfaz. Puede seleccionar tantos como desee. |


4. Elija **Aceptar**.

   La interfaz se crea en el archivo del nombre especificado. Además, la clase seleccionada ahora implementa esa interfaz.

   - C#:

      ![Clase resultante: C#](media/extractinterface-class-cs.png)
      
      
      ![Interfaz resultante: C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Clase resultante: Visual Basic](media/extractinterface-class-vb.png)
      
      
      ![Interfaz resultante: Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
