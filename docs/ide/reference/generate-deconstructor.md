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
ms.openlocfilehash: 8887f4cd6b4dcd7f08e808f1271f5d546d6a224c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159184"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generar un deconstructor en Visual Studio

Esta generación de código se aplica a:

- C#

**Qué:** Permite generar de inmediato el código auxiliar de método de un nuevo deconstructor.

**Cuándo:** Quiere deconstruir correctamente el tipo de forma automática.

**Por qué:** Puede escribir manualmente un deconstructor, aunque esta característica genera el código auxiliar automáticamente con los parámetros de salida correctos.

## <a name="generate-deconstructor"></a>Generar deconstructor

1. Declare un nuevo tipo con los parámetros de salida deseados especificados. Esta declaración produce un error si no hay ninguna instancia de deconstrucción coincidente con la declaración.

   ![Error de deconstructor ausente](media/deconstruct.png)

2. Luego realice alguno de los siguientes procedimientos en el:

   - **Teclado**
      - Con el cursor en la declaración, presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
   - **Mouse**
      - Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones**.
      - Haga clic en el botón ![icono de destornillador](media/screwdriver.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea vacía de la clase.

      ![Generar corrección del código de deconstructor](media/deconstruct-codefix.png)

3. Seleccione **Generar método 'MyInternalClass.Deconstruct'** para generar el deconstructor.

   ![Código de deconstructor resultante](media/deconstruct-result.png)


## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)