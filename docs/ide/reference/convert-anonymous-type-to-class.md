---
title: Conversión de un tipo anónimo en clase
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
monikerRange: '>= vs-2019'
ms.openlocfilehash: 251a011695f6f5056e1fdf8e1a6be36b898b66f5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809216"
---
# <a name="convert-anonymous-type-to-class"></a>Conversión de un tipo anónimo en clase

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** convertir un tipo anónimo en clase.

**Cuándo:** si se tiene un tipo anónimo que se quiere continuar compilando en una clase.

**Por qué:** los tipos anónimos son útiles si solo se usan localmente. A medida que crece el código, es bueno disponer de una manera fácil de promoverlos a una clase.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en un tipo anónimo.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Conversión de un tipo anónimo en clase](media/convert-anon-to-class.png)

2. Presione **ENTRAR** para aceptar la refactorización.

   ![Aceptación de la conversión de un tipo anónimo en clase](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
