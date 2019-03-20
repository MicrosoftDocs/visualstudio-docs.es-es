---
title: Conversión de un tipo anónimo en tupla
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b6f5dd8e53ed2e0695370a1cdcb837609be30035
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154444"
---
# <a name="convert-anonymous-type-to-tuple"></a>Conversión de un tipo anónimo para tupla

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** convertir un tipo anónimo en tupla.

**Cuándo:** si se tiene un tipo anónimo que cualifica como tupla.

**Por qué:** las [tuplas](/dotnet/csharp/tuples) son útiles para no recargar la sintaxis. Esta acción rápida facilita el aprovechamiento de esta característica de C#.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en un tipo anónimo.
2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Conversión de un tipo anónimo en tupla](media/convert-anon-to-tuple.png)

2. Presione **ENTRAR** para aceptar la refactorización.

   ![Conversión de un tipo anónimo en tupla](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
