---
title: Conversión de una instrucción switch en una expresión switch
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir una instrucción switch en una expresión switch de C# 8.0.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 56a1b20854cdd2c1821490bb4972d67bbe912056
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919672"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertir una instrucción switch en una expresión switch

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Convierta una [instrucción switch](/dotnet/csharp/language-reference/keywords/switch) en una [expresión switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions) de C# 8.0.

**Cuándo:** Quiere convertir una instrucción `switch` en una expresión `switch` y viceversa. 

**Por qué:** Si solo usa expresiones, esta refactorización permite una transición fácil desde las instrucciones `switch` tradicionales.

## <a name="how-to"></a>Instrucciones

1. En el archivo de proyecto, [establezca la versión de idioma en la versión preliminar](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) puesto que las expresiones `switch` son una nueva característica de C# 8.0.
2. Coloque el cursor en la palabra clave `switch` y presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Convert switch statement to expression** (Convertir una instrucción switch en una expresión).

   ![Convertir una instrucción switch en una expresión switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
