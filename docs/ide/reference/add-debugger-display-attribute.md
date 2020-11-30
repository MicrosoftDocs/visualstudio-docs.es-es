---
title: Agregar atributo DebuggerDisplay
description: Aprenda a agregar el atributo DebuggerDisplay para controlar cómo la ventana de variables del depurador muestra un objeto, una propiedad o un campo.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fa6baa6e104fca2d3a3b45cac343fd1ceb086271
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871124"
---
# <a name="add-debuggerdisplay-attribute"></a>Adición del atributo DebuggerDisplay

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