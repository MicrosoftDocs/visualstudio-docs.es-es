---
title: Generación de operadores IEquatable para structs
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para generar operadores Equals e IEquatable para estructuras.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28d70c0ea95c9373eb87e6199d53f1b43fadd508
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617206"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Generación de operadores IEquatable al generar Equals para structs

Esta generación de código se aplica a:

- C#

**Qué:** permite generar operadores **Equals** e **IEquatable** para [structs](/dotnet/csharp/language-reference/builtin-types/struct).

**Cuándo:** con una struct agregaremos el elemento IEquatable automáticamente, así como los operadores Equals y Not Equals.

**Por qué:**

- Si implementa un tipo de valor, considere la posibilidad de invalidar el método **Equals** para obtener un mayor rendimiento a través de la implementación predeterminada del método Equals en ValueType.

- La implementación de la interfaz IEquatable implementa un método Equals() específico del tipo.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en algún lugar de la línea de la declaración de struct.

2. A continuación, realice alguno de los siguientes procedimientos:

   - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic en el botón ![icono de destornillador](../media/screwdriver-icon.png) que aparece en el margen izquierdo.

   ![Generación de IEquatable y Equals para structs](media/generate-equals-structs.png)

3. Seleccione **Generar "Equals(object)"** en el menú desplegable.

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)