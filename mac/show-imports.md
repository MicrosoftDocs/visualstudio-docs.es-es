---
title: Visualización de elementos de importación
description: Use Visualización de elementos de importación para expandir IntelliSense en Visual Studio para Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/25/2019
ms.locfileid: "75439107"
---
# <a name="show-import-items"></a>Visualización de elementos de importación

Visual Studio para Mac puede mostrar todos los tipos disponibles, incluso si no se importan al proyecto, en la lista de finalización de IntelliSense. Al seleccionar un elemento que no se importa, se agregará la instrucción `using` correcta al archivo de código fuente.

![Información general de visualización de los elementos de importación](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Cómo habilitar

Para habilitar esta característica, abra **Preferencias** a través de **Visual Studio** > **Preferencias** y vaya a **Editor de texto** > **IntelliSense**. Active la casilla **Visualización de elementos de importación** para habilitar elementos adicionales en IntelliSense.

![opción de visualización de los elementos de importación](media/show-import-items.png)

## <a name="usage"></a>Uso

Una vez que habilite **Visualización de elementos de importación**, el proceso de uso de la característica para importar un elemento es similar a las acciones normales en IntelliSense. A medida que escribe código, los elementos que son válidos rellenarán la lista de finalización. Esto incluye los elementos que todavía no se han importado. Los elementos que no se importan mostrarán su espacio de nombres completo a la derecha del elemento, lo que le permitirá ver qué importaciones está extrayendo al proyecto.

![lista de visualización de los elementos de importación](media/show-import-items-list.png)

En la lista de IntelliSense, los espacios de nombres se muestran junto a los miembros a los que no se hace referencia actualmente mediante una instrucción `using`. Si elige uno de los elementos de la lista, el miembro se agregará al código _y_ la instrucción `using` se agregará a la parte superior del archivo. Los miembros de los tipos a los que ya se hace referencia en el código no mostrarán su espacio de nombres en IntelliSense.

## <a name="see-also"></a>Vea también

- [Acciones rápidas (Visual Studio en Windows)](/visualstudio/ide/quick-actions)
- [Refactorizar código (Visual Studio en Windows)](/visualstudio/ide/refactoring-in-visual-studio)
