---
title: Refactorizar código para reemplazar var por un tipo explícito
ms.date: 05/15/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 893fc2f989dab579690cdac37edae3ba0fad606a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869143"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refactorizar código para reemplazar var por un tipo explícito

Utilice esta refactorización para reemplazar [var](/dotnet/csharp/language-reference/keywords/var) en una declaración de variable local por un tipo explícito.

Esta refactorización se aplica a lo siguiente:

- C#

## <a name="why-to-use-an-explicit-type"></a>Por qué utilizar un tipo explícito

Estos son algunos motivos para declarar una variable con un tipo explícito:

- Para mejorar la legibilidad del código.

- Cuando no quiere inicializar la variable en la declaración.

Aunque debe usarse [var](/dotnet/csharp/language-reference/keywords/var) cuando una variable se inicializa con un tipo anónimo y más adelante se tiene acceso a las propiedades del objeto. Para más información, vea [Variables locales con asignación implícita de tipos (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Cómo se usa

1. Coloque el símbolo de inserción en la palabra clave `var`.

1. Presione **Ctrl**+**.** o haga clic en el icono del destornillador ![icono de destornillador](../media/screwdriver-icon.png) en el margen del archivo de código.

   ![Usar el menú de acciones rápidas de tipo explícito](media/use-explicit-type.png)

1. Seleccione **Usar un tipo explícito**. También puede seleccionar **Vista previa de cambios** para abrir el cuadro de diálogo [Vista previa de cambios](../../ide/preview-changes.md) y, después, seleccionar **Aplicar**.

## <a name="see-also"></a>Vea también

- [Variables con asignación implícita de tipos (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactorización](../refactoring-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)