---
title: Generación de operadores de comparación para tipos que implementan IComparable
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31e33b562a5a11ff77c1d610fbce9e90506b036d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85291026"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>Generación de operadores de comparación para tipos que implementan IComparable

Esta generación de código se aplica a:

- C#

**Qué:** Permite generar operadores de **comparación** para tipos que implementan IComparable.

**Cuándo:** Tiene un tipo que implementa IComparable. Agregaremos automáticamente los operadores de comparación.

**Por qué:** Si implementa un tipo de valor, considere la posibilidad de invalidar el método **Equals** para obtener un mayor rendimiento a través de la implementación predeterminada del método Equals en ValueType.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la clase o en la palabra clave IComparable.

2. A continuación, realice alguno de los siguientes procedimientos:

   - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic en el botón ![icono de destornillador](../media/screwdriver-icon.png) que aparece en el margen izquierdo.

   ![Generación de operadores de comparación](media/generate-comparison-operators.png)

3. Seleccione **Generar "Equals(object)"** en el menú desplegable.

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
