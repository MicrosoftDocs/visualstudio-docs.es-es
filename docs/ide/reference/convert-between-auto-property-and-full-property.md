---
title: Conversión entre propiedad automática y propiedad completa
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir una propiedad implementada automáticamente en una propiedad completa y viceversa.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 3680444c07658da8e77b6058f5a71b9dcf119193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907600"
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
