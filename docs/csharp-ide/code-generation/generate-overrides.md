---
title: "Generar Equals y GetHashCode (método) reemplazos: generación de código (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.openlocfilehash: 88ebbeed4af1d0ea79a27ff21f7ae38ec8c252c1
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2017
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Generar a Equals y GetHashCode (método) se reemplaza en C# #

**¿Qué:** permite generar **es igual a** y **GetHashCode** métodos.

**Cuándo:** generar estas invalidaciones cuando tenga un tipo que representa un "valor" que se debe comparar por algunos campos, en lugar de por la ubicación del objeto en la memoria.

**Por este motivo:** si implementa un tipo de valor, considere la posibilidad de reemplazar el método Equals para obtener un mayor rendimiento a través de la implementación predeterminada del método Equals en ValueType.

Si está implementando un tipo de referencia, considere la posibilidad de reemplazar el método Equals si su tipo es similar a un tipo base, como punto, String, BigNumber y así sucesivamente.

Invalide el método GetHashCode para permitir que un tipo que funcione correctamente en una tabla hash. Lea esta guía, más en [operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators).

**Cómo:**

1. Coloque el cursor en la declaración de tipo.

   ![Código que aparece resaltado](media/overrides_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **generar Equals(object)** o **generar Equals y GetHashCode** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Haga clic en y seleccione el **acciones rápidas y refactorizaciones** menú y seleccione **generar Equals(object)** o **generar Equals y GetHashCode** desde la ventana de vista previa elemento emergente.
     * Haga clic en el botón ![Bombilla](media/bulb.png) icono que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la declaración de tipos.

   ![Generar vista previa de invalidaciones](media/overrides_preview.png)

1. Elegir los miembros que desea generar los métodos de invalidaciones para:

    ![Generar el cuadro de diálogo de invalidaciones](media/overrides_dialog.png)

    > [!TIP]
    > También puede elegir generar operadores desde este cuadro de diálogo mediante las casillas de verificación debajo de la lista de miembros.

1. Equals y GetHashCode invalidaciones se generará con las implementaciones predeterminadas automática.

   ![Generar el resultado del método](media/overrides_result.png)

## <a name="see-also"></a>Vea también

[Code Generation (C#)](../code-generation-csharp.md) (Generación de código (C#))  
[Vista previa de cambios](../../ide/preview-changes.md)
