---
title: Generar instrucciones Using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 9fd34b40bdd1167eca7fa1dff8ab60bcc787b7c7
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324760"
---
# <a name="generate-usings-in-visual-studio"></a>Generar instrucciones Using en Visual Studio

Esta generación de código se aplica a:

- C#

**Qué:** **Qué:** Permite agregar inmediatamente las importaciones necesarias o [instrucciones Using](/dotnet/csharp/language-reference/keywords/using-statement) de código copiado y pegado.

**Cuándo:** Es habitual copiar y pegar código de distintos lugares en el proyecto u otros orígenes de código. Esta acción rápida analiza las importaciones que faltan del código copiado y pegado y luego pide que se agreguen.

**Por qué:** Al agregar automáticamente las importaciones necesarias, el usuario no tiene que copiar manualmente las instrucciones `using` necesarias.

## <a name="generate-usings-refactoring"></a>Generar refactorización de instrucciones Using

1. Copie y pegue código de otro archivo sin incluir las instrucciones `using` necesarias. El error ahora va acompañado de una corrección de código que agrega las instrucciones `using` que faltan.

    > [!NOTE] 
    > Esta sugerencia debe activarse en **Herramientas > Opciones > Editor de texto > C# > Opciones avanzadas > Directivas Using**.

2. Presione **Ctrl**+**.** para abrir el menú **Acciones rápidas y refactorizaciones**. 

    ![Generar instrucciones Using](media/generate-using-codefix.png)

3. Seleccione **using \<su referencia\>;** para agregar la referencia que falta.

    ![Generar resultado de instrucciones Using](media/generate-using-result.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)