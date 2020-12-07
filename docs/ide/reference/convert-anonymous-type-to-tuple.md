---
title: Conversión de un tipo anónimo en tupla
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir un tipo anónimo en una tupla en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 452ba826a2765ef624e6c3d04bb20915a26c51fb
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040867"
---
# <a name="convert-anonymous-type-to-tuple"></a>Conversión de un tipo anónimo para tupla

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** convertir un tipo anónimo en tupla.

**Cuándo:** si se tiene un tipo anónimo que cualifica como tupla.

**Por qué:** las [tuplas](/dotnet/csharp/tuples) son útiles para no recargar la sintaxis. Esta acción rápida facilita el aprovechamiento de esta característica de C#.

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor en un tipo anónimo.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Conversión de un tipo anónimo en tupla](media/convert-anon-to-tuple.png)

2. Presione **ENTRAR** para aceptar la refactorización.

   ![Conversión de un tipo anónimo en tupla aceptada](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
