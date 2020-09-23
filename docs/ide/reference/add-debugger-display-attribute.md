---
title: Agregar atributo DebuggerDisplay
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: db49bfd1672866a755cce6780527520da2cad420
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810394"
---
# <a name="add-debuggerdisplay-attribute"></a>Agregar atributo DebuggerDisplay

Esta generación de código se aplica a:

- C#

**Qué:** el [atributo DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) controla la forma en que se muestra un objeto, una propiedad o un campo en las ventanas de variables del depurador.

**Cuándo:** si desea [anclar propiedades](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) del depurador mediante programación en el código.

**Por qué:** anclar propiedades permite inspeccionar rápidamente los objetos por sus propiedades mediante la propagación de esa propiedad en la parte superior de la lista de propiedades del objeto en el depurador. 

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en un tipo, delegado, delegado, propiedad o campo. 

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Agregar atributo DebuggerDisplay**.

    ![Generación de operadores de comparación](media/add-debugger-display-attribute.png)

3. El atributo DebuggerDisplay se agregará junto con un método auto que devuelve la sintaxis ToString() predeterminada. 

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)