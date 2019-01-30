---
title: Generación de un método
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c2de6f8608857d102454d03a98aacd175a22cef
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024947"
---
# <a name="generate-a-method-in-visual-studio"></a>Generación de un método en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Permite agregar inmediatamente un método a una clase.

**Cuándo:** Se introduce un método nuevo y se quiere declarar de manera adecuada y de inmediato.

**Por qué:** Se podría declarar el método y los parámetros antes de usarlo; pero esta característica generará la declaración de forma automática.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la línea donde haya un subrayado ondulado de color rojo. Este subrayado ondulado de color rojo señala un método que aún no existe.

   - C#:

       ![Código resaltado (C#)](media/method-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (VB)](media/method-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece.
      - Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

      ![Vista previa de la generación de método](media/method-preview-cs.png)

3. Seleccione **Generar método** en el menú desplegable.

   > [!TIP]
   > Use el vínculo **Vista previa de los cambios** en la parte inferior de la ventana de vista previa [para ver todos los cambios ](../../ide/preview-changes.md) que se aplicarán antes de realizar la selección.

   El método se crea con los parámetros que se deducen de su uso.

   - C#:

       ![Resultado de la generación de método (C#)](media/method-result-cs.png)

   - Visual Basic:

       ![Resultado de la generación de método (VB)](media/method-result-vb.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)