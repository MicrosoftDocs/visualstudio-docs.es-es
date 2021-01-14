---
title: Cuadro de diálogo Al visitar un punto de interrupción | Microsoft Docs
description: Use "Al visitar un punto de interrupción" para especificar qué acción se realizará cuando se produzca la interrupción. Puede especificar que se imprima un mensaje y que la ejecución continúe después.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a528709769f599219a7b3df2b8157b0ee3a605b1
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149318"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Al visitar un punto de interrupción (Cuadro de diálogo)
Con este cuadro de diálogo, es posible personalizar la acción que ocurre cuando se visita un punto de interrupción.

## <a name="uielement-list"></a>Lista de UIElement
 **Imprimir un mensaje**: imprime un mensaje con la sintaxis de DebuggerDisplay. Para obtener más información, vea [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Este cuadro de texto también admite palabras clave especiales (como $ADDRESS), que se pueden utilizar por sí solas o dentro de las llaves de una expresión DebuggerDisplay. Las palabras clave disponibles se muestran en el cuadro de diálogo.

 **Continuar la ejecución**: este control solo se habilita cuando se selecciona **Imprimir un mensaje**. Cuando este control está seleccionado, se puede utilizar un punto de interrupción como punto de seguimiento para hacer un seguimiento la ejecución de programas, en lugar de interrumpirla cuando se visita la ubicación.

## <a name="see-also"></a>Vea también
- [Usar puntos de interrupción](../debugger/using-breakpoints.md)
- [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)