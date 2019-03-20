---
title: Generar instrucciones Using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f59dceabb076ebce36755c41caa6de00258be883
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160646"
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