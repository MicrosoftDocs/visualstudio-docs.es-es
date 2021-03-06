---
title: Extracción de la clase base
description: Esta refactorización extrae los miembros de una clase seleccionada a una nueva clase base.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9d7a21bbd3e51ee6a6776ca728a545cbbb731cab
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466282"
---
# <a name="extract-base-class"></a>Extracción de la clase base

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Extraer la clase base.

**Cuándo:** Quiere extraer miembros de una clase seleccionada a una nueva clase base.

**Por qué:** La extracción manual de miembros puede llevar mucho tiempo e interrumpir su flujo de trabajo. 

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor de inserción en el nombre de la clase o en un miembro resaltado.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione **Extraer miembros a una nueva clase base**.

    ![Cuadro de diálogo Extract base clase (Extraer clase base)](media/extract-base-class.png)

Se abrirá el nuevo cuadro de diálogo **Extract Base Class** (Extraer clase base), donde puede especificar el nombre de la clase base y la ubicación donde debe colocarse. Puede seleccionar los miembros que quiere transferir a la nueva clase base y elegir que los miembros sean abstractos activando la casilla de la columna Make abstract (Convertir en abstracto).

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
