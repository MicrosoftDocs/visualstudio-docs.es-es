---
title: Convertir miembro en estático
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1ecc66cb58ad11bd431acb341dae0493ce8192da
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77519306"
---
# <a name="make-member-static"></a>Convertir miembro en estático

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** convierta un miembro en estático.

**Cuándo:** quiere que un miembro no estático sea estático.

**Por qué:** los miembros estáticos mejoran la legibilidad; el saber que un código específico está aislado facilita su comprensión, relectura y reutilización. 

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor de inserción sobre el nombre del miembro.

2. Presione **Ctrl**+ **.** (punto) para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Convertir miembro en estático](media/make-member-static.png)

3. Seleccione **Hacer estático**.

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
