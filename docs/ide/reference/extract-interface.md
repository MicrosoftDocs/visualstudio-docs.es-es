---
title: Refactorización de extracción de una interfaz
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para crear una interfaz mediante los miembros existentes de una clase, estructura o interfaz.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 13e9b684c81abf491b5836c96190c6a89bdc0643
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617401"
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
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Extraer interfaz** en el menú emergente de la ventana Vista previa.
   - **Mouse**
      - Seleccione **Editar > Refactorizar > Extraer interfaz**.
      - Haga clic con el botón derecho en el nombre de la clase, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Extraer interfaz** en el menú emergente de la ventana Vista previa.

3. En el cuadro de diálogo **Extraer interfaz** que se abre, escriba la información que se le pide:

   ![Extraer interfaz](media/extractinterface-dialog-same-file.png)

   | Campo | Descripción |
   | - | - |
   | **Nuevo nombre de interfaz** | Nombre de la interfaz que se va a crear. El nombre predeterminado es I *ClassName*, donde *ClassName* es el nombre de la clase seleccionada anteriormente. |
   | **Nuevo nombre de archivo** | Nombre del archivo generado que va a incluir la interfaz. Al igual que el nombre de interfaz, el nombre predeterminado es I *ClassName*, donde *ClassName* es el nombre de la clase seleccionada anteriormente. También puede seleccionar la opción **Agregar al archivo actual**. |
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
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)
