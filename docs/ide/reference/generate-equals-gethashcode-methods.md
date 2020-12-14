---
title: Generar invalidaciones de los métodos Equals y GetHashCode de C#
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para generar métodos Equals y GetHashCode.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f6f7ec74af21ef62079a3fef18dd39544e7b42aa
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617518"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generación de invalidaciones de los métodos Equals y GetHashCode en Visual Studio

Esta generación de código se aplica a:

- C#

**Qué:** Le permite generar métodos **Equals** y **GetHashCode**.

**Cuándo:** Genere estas invalidaciones cuando tenga un tipo que deba compararse por uno o más campos, en lugar de por la ubicación del objeto en la memoria.

**Por qué:**

- Si implementa un tipo de valor, considere la posibilidad de invalidar el método **Equals** para obtener un mayor rendimiento a través de la implementación predeterminada del método Equals en ValueType.

- Si está implementando un tipo de referencia, considere la posibilidad de invalidar el método **Equals** si su tipo es similar a un tipo base, como Point, String, BigNumber, etc.

- Invalide el método **GetHashCode** para permitir que un tipo funcione correctamente en una tabla hash. Obtenga más información sobre los [operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor en algún lugar de la línea de la declaración de tipos.

   ![Código resaltado](media/overrides-highlight-cs.png)

   > [!TIP]
   > No haga doble para seleccionar el nombre del tipo o la opción de menú no estará disponible. Simplemente coloque el cursor en algún lugar de la línea.

1. A continuación, realice alguno de los siguientes procedimientos:

   - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic en el botón ![icono de destornillador](../media/screwdriver-icon.png) que aparece en el margen izquierdo.

   ![Vista previa de la generación de invalidaciones](media/overrides-preview-cs.png)

1. Seleccione **Generar Equals(object)** o **Generar Equals y GetHashCode** en el menú desplegable.

1. En el cuadro de diálogo **Seleccionar miembros**, seleccione los miembros para los que quiere generar los métodos:

    ![Cuadro de diálogo de generación de invalidaciones](media/overrides-dialog-cs.png)

    > [!TIP]
    > También puede generar operadores desde este cuadro de diálogo con las casillas de verificación de la parte inferior del mismo.

   Los métodos `Equals` y `GetHashCode` se generan con implementaciones predeterminadas.

   ![Resultado de la generación de método](media/overrides-result-cs.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
