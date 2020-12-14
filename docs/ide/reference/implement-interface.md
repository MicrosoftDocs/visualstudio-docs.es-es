---
title: Implementar una interfaz
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para generar inmediatamente el código necesario para implementar una interfaz.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0484ed5f63cd4651669a8e3c1f94f5aad96fcc03
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617115"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementación de una interfaz en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Le permite generar inmediatamente el código necesario para implementar una interfaz.

**Cuándo:** Desea heredar de una interfaz.

**Por qué:** Podría implementar manualmente todas las interfaces una por una, sin embargo, esta característica generará automáticamente todas las firmas de método de manera automática.

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo, que señala que ha hecho referencia a una interfaz, pero que no ha implementado todos los miembros requeridos.

   - C#:

       ![Código resaltado (C#)](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (VB)](media/interface-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![bombilla de error](media/error-bulb.png) que aparece.
      - Haga clic en el botón ![bombilla de error](media/error-bulb.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

3. Seleccione **Implementar interfaz** en el menú desplegable.

   ![Vista previa de implementación de interfaz](media/interface-preview-cs.png)

   > [!TIP]
   > - Use el vínculo **Vista previa de los cambios** en la parte inferior de la ventana de vista previa [para ver todos los cambios](../../ide/preview-changes.md) que se aplicarán antes de realizar la selección.
   > - Use los vínculos **Documento**, **Proyecto** y **Solución** de la parte inferior de la ventana de vista previa para crear las firmas de método adecuadas entre las múltiples clases que implementan la interfaz.

   Las firmas de método de la interfaz se crean y están listas para su implementación.

   - C#:

       ![Resultado de implementación de interfaz (C#)](media/interface-result-cs.png)

   - Visual Basic:

       ![Resultado de implementación de interfaz (VB)](media/interface-result-vb.png)

   > [!TIP]
   > (Solo C#) Use la opción **Implementar la interfaz de forma explícita** para colocar delante de cada método generado el nombre de la interfaz y, así, evitar conflictos de nombres.
   >
   > ![Resultado de la implementación de la interfaz de forma explícita](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
