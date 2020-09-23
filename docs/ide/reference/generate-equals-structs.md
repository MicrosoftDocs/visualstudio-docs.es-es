---
title: Generación de operadores IEquatable para structs
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5ee695169f52036858fc70598f81f375638ab03f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808121"
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