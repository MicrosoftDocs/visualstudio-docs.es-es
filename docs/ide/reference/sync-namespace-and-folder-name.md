---
title: Sincronización de espacio de nombres y nombre de carpeta
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d7073edaf6ecc261c58bf1e5607323b9214c5ed0
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160761"
---
# <a name="sync-namespace-and-folder-name"></a>Sincronización de espacio de nombres y nombre de carpeta

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** sincronización de espacio de nombres y nombre de carpeta.

**Cuándo:** desea rediseñar partes de su solución arrastrando un archivo a una nueva carpeta. 

**Por qué:** desea asegurarse de que su espacio de nombres se mantiene actualizado con su nueva estructura de carpetas.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en el nombre del espacio de nombres.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Change namespace to \<folder name>** (Cambiar el espacio de nombres por <nombre de carpeta>).

   ![Sincronización de espacio de nombres y nombre de carpeta](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
