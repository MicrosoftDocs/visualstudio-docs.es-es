---
title: Convertir miembro en estático
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir un miembro en estático.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5478e85d89d4ea44d34e0a5ae9170aaffb3836f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919452"
---
# <a name="make-member-static"></a>Convertir miembro en estático

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** convierta un miembro en estático.

**Cuándo:** quiere que un miembro no estático sea estático.

**Por qué:** los miembros estáticos mejoran la legibilidad; el saber que un código específico está aislado facilita su comprensión, relectura y reutilización. 

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor de inserción sobre el nombre del miembro.

2. Presione **Ctrl**+ **.** (punto) para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Convertir miembro en estático](media/make-member-static.png)

3. Seleccione **Hacer estático**.

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
