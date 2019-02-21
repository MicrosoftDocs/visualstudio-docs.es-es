---
title: Conversión de un tipo anónimo en clase
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e3613f365b2510111f6854087a597df387ab1a4c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335885"
---
# <a name="convert-anonymous-type-to-class"></a>Conversión de un tipo anónimo en clase

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** convertir un tipo anónimo en clase.

**Cuándo:** si se tiene un tipo anónimo que se quiere continuar compilando en una clase.

**Por qué:** los tipos anónimos son útiles si solo se usan localmente. A medida que crece el código, es bueno disponer de una manera fácil de promoverlos a una clase.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en un tipo anónimo.
2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Conversión de un tipo anónimo en clase](media/convert-anon-to-class.png)

2. Presione **ENTRAR** para aceptar la refactorización.

   ![Aceptación de la conversión de un tipo anónimo en clase](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
