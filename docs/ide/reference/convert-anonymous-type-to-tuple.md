---
title: Conversión de un tipo anónimo en tupla
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir un tipo anónimo en una tupla en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6486b771207722c64993d5a880894fe07beb99c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907666"
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
