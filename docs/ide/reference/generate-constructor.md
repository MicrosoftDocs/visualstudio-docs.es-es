---
title: Acción rápida Generación de un constructor
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6c7f46bd93e476c3f9ffe08831c5016a449ee4bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895303"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Generación de un constructor en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Permite generar el código de inmediato para un nuevo constructor en una clase.

**Cuándo:** Se inserta un nuevo constructor y se quiere declarar adecuadamente de manera automática, o se modifica un constructor existente.

**Por qué:** Se podría declarar el constructor antes de usarlo, aunque esta característica lo genera, con los parámetros adecuados, automáticamente. Además, la modificación de un constructor existente requiere la actualización de todos los sitios de llamada, a menos que utilice esta característica para actualizarlos automáticamente.

**Cómo**: Hay varias maneras de generar un constructor:

   - [Generación de constructor y selección de miembros](#pick)
   - [Generación de constructor a partir de campos seleccionados](#selection)
   - [Generación de constructor a partir de nuevo uso](#usage)
   - [Adición de parámetro a constructor existente](#addparameter)
   - [Creación e inicialización de campo/propiedad a partir de un parámetro de constructor](#create)

## <a id = "pick"></a> Generación de constructor y selección de miembros (solo C#)

1. Coloque el cursor en cualquier línea vacía de una clase:

   ![Cursor en una línea vacía](media/constructor1-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea vacía de la clase.

   ![Vista previa de generación de constructor](media/constructor1-preview-cs.png)

1. Seleccione **Generar constructor** en el menú desplegable.

   Se abre el cuadro de diálogo **Seleccionar miembros**.

1. Seleccione los miembros que quiera incluir como parámetros del constructor. Puede ordenarlos con las flechas arriba y abajo. Elija **Aceptar**.

   ![Cuando de diálogo Selección de miembros](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Puede activar la casilla **Agregar comprobaciones de valores null** para generar automáticamente comprobaciones de valores null para los parámetros de constructor.

   El constructor se crea con los parámetros seleccionados.

   ![Resultado de la generación de constructor](media/constructor1-result-cs.png)

## <a id="selection"></a> Generación de constructor a partir de campos seleccionados (solo C#)

1. Resalte los miembros que quiera tener en su constructor generado:

   ![Resaltar miembros](media/constructor2-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la selección.

      ![Vista previa de generación de constructor](media/constructor2-preview-cs.png)

1. Seleccione **Generar constructor "TypeName(...)"** en el menú desplegable.

   El constructor se crea con los parámetros seleccionados.

   ![Resultado de la generación de constructor](media/constructor2-result-cs.png)

## <a id="usage"></a> Generación de constructor a partir de nuevo uso (C# y Visual Basic)

1. Coloque el cursor en la línea donde haya un subrayado ondulado de color rojo. El subrayado ondulado de color rojo señala una llamada a un constructor que aún no existe.

   - C#:

       ![Código resaltado (C#)](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (VB)](media/constructor-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece.
      - Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

      ![Vista previa de generación de constructor](media/constructor-preview-cs.png)

3. Seleccione **Generar constructor en "*TypeName*"** en el menú desplegable.

   > [!TIP]
   > Use el vínculo **Vista previa de los cambios** en la parte inferior de la ventana de vista previa [para ver todos los cambios ](../../ide/preview-changes.md) que se aplicarán antes de realizar la selección.

   El constructor se crea con los parámetros que se deducen de su uso.

   - C#:

       ![Resultado de la generación de método (C#)](media/constructor-result-cs.png)

   - Visual Basic:

       ![Resultado de la generación de método (VB)](media/constructor-result-vb.png)

## <a id="addparameter"></a> Adición de parámetro a constructor existente (solo C#)

1. Agregue un parámetro a una llamada de constructor existente.

2. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha utilizado un constructor que aún no existe.

    ![Destacado de generación de constructor](media/constructor4-highlight-cs.png)

3. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece.
      - Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

      ![Vista previa de generación de constructor](media/constructor4-preview-cs.png)

4. Seleccione **Agregar parámetro a "TypeName(...)"** en el menú desplegable.

   El parámetro se agrega al constructor con su tipo inferido a partir de su uso.

   ![Resultado de la generación de constructor](media/constructor4-result-cs.png)

También puede agregar un parámetro a un método existente. Para más información, consulte [Incorporación de un parámetro a un método](add-parameter.md).

## <a id="create"></a> Creación e inicialización de campo o propiedad a partir de un parámetro de constructor (solo C#)

1. Busque un constructor existente y agregue un parámetro:

   ![Destacado de generación de constructor](media/constructor5-highlight-cs.png)

1. Coloque el cursor dentro del parámetro recién agregado.

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el parámetro agregado.

   ![Vista previa de generación de constructor](media/constructor5-preview-cs.png)

1. Seleccione **Crear e inicializar propiedad** o **Crear e inicializar campo** en el menú desplegable.

   El campo o la propiedad se declaran y se les asignará automáticamente un nombre que coincida con sus tipos. También se agrega una línea de código para inicializar el campo o la propiedad en el cuerpo del constructor.

   ![Resultado de la generación de constructor](media/constructor5-result-cs.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)