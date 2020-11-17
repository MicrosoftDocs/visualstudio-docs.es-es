---
title: Conversión de la clase en abstracta
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8bfcaa7117249ceffbaed706ac420c5250c02089
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403577"
---
# <a name="make-class-abstract"></a>Conversión de la clase en abstracta

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Refactorización de la conversión de la clase en abstracta.

**Cuándo:** Escribe un método abstracto en una clase que no es abstracta.

**Por qué:**  Tener una corrección de código para convertir una clase en abstracta después de escribir un método abstracto le ahorrará tiempo.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor de inserción en el método abstracto.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione **Make class 'abstract'** (Convertir la clase en "abstracta").

    ![Conversión de la clase en abstracta](media/make-class-abstract.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
