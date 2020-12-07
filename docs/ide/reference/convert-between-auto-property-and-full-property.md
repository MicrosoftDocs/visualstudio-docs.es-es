---
title: Conversión entre propiedad automática y propiedad completa
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir una propiedad implementada automáticamente en una propiedad completa y viceversa.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b53f337b538ff1c0aef84272eea7d9e032eb2c1d
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040841"
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
