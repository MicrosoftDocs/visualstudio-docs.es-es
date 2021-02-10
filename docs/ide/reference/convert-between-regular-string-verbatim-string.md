---
title: Conversión entre literales de cadenas regulares y textuales
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para realizar conversiones entre literales de cadenas regulares y literales de cadenas textuales.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1c335c90183e4c5c97b1a2737a2edd8a1b86fb77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918330"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>Conversión entre literales de cadenas regulares y literales de cadenas textuales: refactorización

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** vamos a realizar la conversión entre literales de cadenas regulares y literales de cadenas textuales.

**Cuándo:** quiere ahorrar espacio o proporcionar mayor claridad en el código.

**Por qué:** la conversión de un literal de cadena textual en un literal de cadena regular puede ayudar a ahorrar espacio. Convertir un literal de cadena regular en un literal de cadena textual puede proporcionar mayor claridad.

## <a name="how-to"></a>Procedimiento

1. Coloque el símbolo de intercalación en el literal de cadena regular o en el literal de cadena textual:

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione una de las opciones siguientes:

    Seleccione **Convert to regular string** (Convertir en cadena normal).

    ![Conversión en cadena regular](media/convert-to-regular-string.png)

    Seleccione **Convert to verbatim string** (Convertir en cadena textual).

    ![Conversión en cadena textual](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)