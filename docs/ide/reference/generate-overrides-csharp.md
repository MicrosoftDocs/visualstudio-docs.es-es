---
title: "Generación de invalidaciones de los métodos Equals y GetHashCode: generación de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 56b1753dbdcfbf8ce318e964a16879f02b1482c4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Generación de invalidaciones de los métodos Equals y GetHashCode en C# #

**Qué:** Le permite generar métodos **Equals** y **GetHashCode**.

**Cuándo:** Genere estas invalidaciones cuando tenga un tipo que representa un "valor" que se debe comparar por algunos campos, en lugar de por la ubicación del objeto en la memoria.

**Por qué:** si implementa un tipo de valor, considere la posibilidad de invalidar el método Equals para obtener un mayor rendimiento a través de la implementación predeterminada del método Equals en TipoValor.

Si está implementando un tipo de referencia, considere la posibilidad de invalidar el método Equals si su tipo es similar a un tipo base, como Point, String, BigNumber, etc.

Invalide el método GetHashCode para permitir que un tipo funcione correctamente en una tabla hash. Obtenga más información sobre los [operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators).

**Cómo**:

1. Coloque el cursor en la declaración de tipo.

   ![Código resaltado](media/overrides-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Generar "Equals(object)"** o **Generar Equals y GetHashCode** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione **Acciones rápidas y refactorizaciones** y elija **Generar "Equals(object)"** o **Generar Equals y GetHashCode** en el menú emergente de la ventana Vista previa.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la declaración de tipo.

   ![Vista previa de la generación de invalidaciones](media/overrides-preview-cs.png)

1. Seleccione los miembros para los que desea generar los métodos de las invalidaciones:

    ![Cuadro de diálogo de generación de invalidaciones](media/overrides-dialog-cs.png)

    > [!TIP]
    > También puede optar por generar operadores desde este cuadro de diálogo mediante las casillas de verificación que están debajo de la lista de miembros.

1. Las invalidaciones Equals y GetHashCode se generarán con las implementaciones predeterminadas automáticas.

   ![Resultado de la generación de método](media/overrides-result-cs.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)
