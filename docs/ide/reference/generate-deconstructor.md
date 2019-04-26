---
title: Acción rápida Generar un deconstructor
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2ca2d3a0c174fa4c7d0f66d3abc440b8c9aa93cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790421"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generar un deconstructor en Visual Studio

Esta generación de código se aplica a:

- C#

**Qué:** Permite generar de inmediato el código auxiliar de método de un nuevo deconstructor.

**Cuándo:** Quiere deconstruir correctamente el tipo de forma automática.

**Por qué:** Puede escribir manualmente un deconstructor, aunque esta característica genera el código auxiliar automáticamente con los parámetros de salida correctos.

## <a name="generate-a-deconstructor"></a>Generar un deconstructor

1. Declare un nuevo tipo con los parámetros de salida deseados especificados. Esta declaración produce un error si no se encuentra ninguna instancia de deconstrucción coincidente con la declaración.

   ![Error de deconstructor ausente](media/deconstruct.png)

2. Elija uno de los siguientes pasos:

   - **Teclado**
      - Con el cursor en la declaración, seleccione Ctrl+. para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Seleccione el ![icono de destornillador](media/screwdriver.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea vacía de la clase.

      ![Generar corrección del código de deconstructor](media/deconstruct-codefix.png)

3. Seleccione **Generar método 'MyInternalClass.Deconstruct'** para generar el deconstructor.

   ![Código de deconstructor resultante](media/deconstruct-result.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)