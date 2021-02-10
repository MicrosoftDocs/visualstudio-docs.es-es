---
title: Implementación de una clase abstracta
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para generar inmediatamente el código necesario para implementar una clase abstracta.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 05527e8ab1414b3f372f6db22c258d51fcd119a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852510"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementación de una clase abstracta en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Le permite generar inmediatamente el código necesario para implementar una clase abstracta.

**Cuándo:** Desea heredar de una clase abstracta.

**Por qué:** Podría implementar manualmente todos los miembros abstractos uno por uno, sin embargo, esta característica generará automáticamente todas las firmas de método de manera automática.

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo, que señala que ha heredado de una clase abstracta, pero que no ha implementado todos los miembros requeridos.

   - C#:

       ![Código resaltado (C#)](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (VB)](media/abstract-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![bombilla de error](media/error-bulb.png) que aparece.
      - Haga clic en el botón ![bombilla de error](media/error-bulb.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

   ![Vista previa de la implementación de la clase](media/abstract-preview-cs.png)

3. Seleccione **Implementar clase abstracta** en el menú desplegable.

   > [!TIP]
   > - Use el vínculo **Vista previa de los cambios** en la parte inferior de la ventana de vista previa [para ver todos los cambios](../../ide/preview-changes.md) que se aplicarán antes de realizar la selección.
   > - Use los vínculos **Documento**, **Proyecto** y **Solución** de la parte inferior de la ventana de vista previa para crear las firmas de método adecuadas entre las múltiples clases que heredan de la clase abstracta.

   Las firmas de método abstracto se crean y están listas para su implementación.

   - C#:

       ![Resultado de la implementación de la clase (C#)](media/abstract-result-cs.png)

   - Visual Basic:

       ![Resultado de la implementación de la clase (VB)](media/abstract-result-vb.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
