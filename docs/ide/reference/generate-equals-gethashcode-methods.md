---
title: Generación de invalidaciones de los métodos Equals y GetHashCode de C# en Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cdbb5273d046be8f11cc2fbc4a03ed6767a31e00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945316"
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

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la declaración de tipo.

   ![Código resaltado](media/overrides-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
     - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
     - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
     - Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la declaración de tipo.

   ![Vista previa de la generación de invalidaciones](media/overrides-preview-cs.png)

1. Seleccione **Generar Equals(object)** o **Generar Equals y GetHashCode** en el menú desplegable.

1. En el cuadro de diálogo **Seleccionar miembros**, seleccione los miembros para los que quiere generar los métodos:

    ![Cuadro de diálogo de generación de invalidaciones](media/overrides-dialog-cs.png)

    > [!TIP]
    > También puede optar por generar operadores desde este cuadro de diálogo mediante las casillas de verificación que están debajo de la lista de miembros.

   Las invalidaciones Equals y GetHashCode se generan con las implementaciones predeterminadas.

   ![Resultado de la generación de método](media/overrides-result-cs.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)