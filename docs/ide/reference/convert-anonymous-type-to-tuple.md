---
title: Conversión de un tipo anónimo en tupla
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b7a53aa8f329c1cdedc0cedff7e56b3f6dfa2f2a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335874"
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
