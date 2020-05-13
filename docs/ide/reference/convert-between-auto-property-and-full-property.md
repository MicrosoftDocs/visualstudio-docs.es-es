---
title: Conversión entre propiedad automática y propiedad completa
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395740"
---
# <a name="convert-between-auto-property-and-full-property"></a>Conversión entre propiedad automática y propiedad completa

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** convierta una propiedad implementada automáticamente en una propiedad completa.

**Cuándo:** la lógica de la propiedad ha cambiado.

**Por qué:** se puede convertir manualmente una propiedad implementada automáticamente en una propiedad completa; sin embargo, esta característica realizará el trabajo automáticamente. 

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor sobre el nombre de la propiedad.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione una de las dos opciones siguientes: 

    Seleccione **Convertir en propiedad completa**.

   ![Convertir propiedad automática en propiedad completa](media/convert-auto-property-to-full-property.png) 

    Seleccione **Usar propiedad automática**. 

    ![Conversión de propiedad completa en propiedad automática](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
