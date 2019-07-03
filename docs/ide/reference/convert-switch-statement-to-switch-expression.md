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
ms.openlocfilehash: ecb7750301101a2607c17e68b5e919623a03caba
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329058"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Conversión de una instrucción switch en una expresión switch

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Convierta una [instrucción switch](/dotnet/csharp/language-reference/keywords/switch) en una [expresión switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) de C# 8.0.

**Cuándo:** Quiere convertir una instrucción `switch` en una expresión `switch` y viceversa. 

**Por qué:** Si solo usa expresiones, esta refactorización permite una transición fácil desde las instrucciones `switch` tradicionales.

## <a name="how-to"></a>Procedimiento

1. En el archivo de proyecto, [establezca la versión de idioma en la versión preliminar](/dotnet/csharp/language-reference/configure-language-version#set-the-language-version-in-visual-studio) puesto que las expresiones `switch` son una nueva característica de C# 8.0.
2. Coloque el cursor en la palabra clave `switch` y presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Convert switch statement to expression** (Convertir una instrucción switch en una expresión).

   ![Convertir una instrucción switch en una expresión switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
