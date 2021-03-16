---
title: Generar invalidaciones de los métodos Equals y GetHashCode de C#
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para generar métodos Equals y GetHashCode.
ms.custom: SEO-VS-2020
ms.date: 03/08/2021
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 6a9d0ea6f6cb0aedc4fa13a8014b1a8bd66ccca0
ms.sourcegitcommit: 6ed6ae5a1693607dce57923a78d01eea3d88b29a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514972"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generación de invalidaciones de los métodos Equals y GetHashCode en Visual Studio

Esta generación de código se aplica a:

- C#

**Qué:** Le permite generar métodos **Equals** y **GetHashCode**.

**Cuándo:** Genere estas invalidaciones cuando tenga un tipo que deba compararse por uno o más campos, en lugar de por la ubicación del objeto en la memoria.

**Por qué:**

- Si está implementando un tipo de valor, considere la posibilidad de invalidar el método **Equals**. Puede aumentar el rendimiento de la implementación predeterminada del método Equals en ValueType al hacerlo.

- Si está implementando un tipo de referencia, considere la posibilidad de invalidar el método **Equals** si su tipo es similar a un tipo base, como Point, String, BigNumber, etc.

- Invalide el método **GetHashCode** para permitir que un tipo funcione correctamente en una tabla hash. Obtenga más información sobre los [operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor en algún lugar de la línea de la declaración de tipos.

    ```csharp
    public class ImaginaryNumber
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }
    }
    ```

   El código debe ser similar al de la siguiente captura de pantalla:

   ![Captura de pantalla del código resaltado en el que se va a aplicar el método generado](media/overrides-highlight-cs.png)

   > [!TIP]
   > No haga doble para seleccionar el nombre del tipo o la opción de menú no estará disponible. Simplemente coloque el cursor en algún lugar de la línea.

1. A continuación, elija una de las acciones siguientes:

   - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.

   - Haga clic en el botón ![Captura de pantalla del icono de destornillado de acciones rápidas en Visual Studio](../media/screwdriver-icon.png) que aparece en el margen izquierdo.

1. Seleccione **Generar Equals(object)** o **Generar Equals y GetHashCode** en el menú desplegable.

   ![Captura de pantalla del menú desplegable Generar invalidaciones](media/overrides-preview-cs.png)

1. En el cuadro de diálogo **Seleccionar miembros**, seleccione los miembros para los que quiere generar los métodos:

    ![Cuadro de diálogo de generación de invalidaciones](media/overrides-dialog-cs.png)

    > [!TIP]
    > También puede generar operadores desde este cuadro de diálogo con las casillas de verificación de la parte inferior del mismo.

   Los métodos `Equals` y `GetHashCode` se generan con implementaciones predeterminadas, como se muestra en el código siguiente:

    ```csharp
   public class ImaginaryNumber : IEquatable<ImaginaryNumber>
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }

        public override bool Equals(object obj)
        {
            return Equals(obj as ImaginaryNumber);
        }

        public bool Equals(ImaginaryNumber other)
        {
            return other != null &&
                   RealNumber == other.RealNumber &&
                   ImaginaryUnit == other.ImaginaryUnit;
        }

        public override int GetHashCode()
        {
            return HashCode.Combine(RealNumber, ImaginaryUnit);
        }
    }
    ```

   El código debe ser similar al de la siguiente captura de pantalla:

   ![Captura de pantalla del resultado del método generado](media/overrides-result-cs.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
