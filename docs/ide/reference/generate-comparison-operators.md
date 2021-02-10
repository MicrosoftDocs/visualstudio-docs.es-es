---
title: Generar operadores de comparación para IComparable
ms.custom: SEO-VS-2020
description: Para aumentar el rendimiento, genere operadores de comparación para los tipos que implementan IComparable.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ee0ac916bcc13e6bc89485171b2ce145b31dd919
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932571"
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
