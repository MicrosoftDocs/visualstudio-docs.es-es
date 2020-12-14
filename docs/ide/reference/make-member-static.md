---
title: Convertir miembro en estático
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir un miembro en estático.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e663d59f47728bc4a7c84290ee0e89ae453f23ae
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561024"
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
