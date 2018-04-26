---
title: Generación de un campo, una propiedad o una variable local en Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4cff83eb490f8012e8679dbd0b2c6a65d27f8e14
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Generación de un campo, una propiedad o una variable local en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Le permite generar inmediatamente el código para un campo, una propiedad o un valor local no declarados previamente.

**Cuándo:** Introduce un nuevo campo, propiedad o valor local mientras escribe y desea declararlo de manera adecuada y de inmediato.

**Por qué:** Podría declarar el campo, la propiedad o el valor local antes de usarlos; sin embargo, esta característica generará la declaración y el tipo automáticamente.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la línea donde haya un subrayado ondulado de color rojo. El subrayado ondulado de color rojo señala un campo, una variable local o una propiedad que aún no existe.

   - C#:

    ![Código resaltado (C#)](media/field-highlight-cs.png)

   - Visual Basic:

    ![Código resaltado (VB)](media/field-highlight-vb.png)

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
     - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
     - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
     - Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece.
     - Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

    ![Vista previa de la generación de campo, propiedad o valor local](media/field-preview-cs.png)

1. Seleccione una de las opciones de generación del menú desplegable.

   > [!TIP]
   > Use el vínculo **Vista previa de los cambios** en la parte inferior de la ventana de vista previa [para ver todos los cambios ](../../ide/preview-changes.md) que se aplicarán antes de realizar la selección.

   El campo, la propiedad o la variable local se crea con el tipo que se deduce de su uso.

   - C#:

      ![Resultado de la generación de método (C#)](media/field-result-cs.png)

   - Visual Basic:

      ![Resultado de la generación de método (VB)](media/field-result-vb.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)