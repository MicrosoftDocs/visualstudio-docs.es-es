---
title: Conversión de una instrucción switch en una expresión switch
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cc13cffe8352d9fb57f5bb991c3af615eddb2a14
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740050"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Conversión de una instrucción switch en una expresión switch

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Convierta una [instrucción switch](/dotnet/csharp/language-reference/keywords/switch) en una [expresión switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) de C# 8.0.

**Cuándo:** Quiere convertir una instrucción `switch` en una expresión `switch` y viceversa. 

**Por qué:** Si solo usa expresiones, esta refactorización permite una transición fácil desde las instrucciones `switch` tradicionales.

## <a name="how-to"></a>Procedimiento

1. En el archivo de proyecto, [establezca la versión de idioma en la versión preliminar](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) puesto que las expresiones `switch` son una nueva característica de C# 8.0.
2. Coloque el cursor en la palabra clave `switch` y presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Convert switch statement to expression** (Convertir una instrucción switch en una expresión).

   ![Convertir una instrucción switch en una expresión switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
