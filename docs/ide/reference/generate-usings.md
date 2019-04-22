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
ms.openlocfilehash: 0ce1b620a6d8aba7e4aea767745891dff6d9f869
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537509"
---
# <a name="generate-usings-in-visual-studio"></a>Generar instrucciones Using en Visual Studio

Esta generación de código se aplica a:

- C#

**Qué:** Permite agregar inmediatamente las instrucciones import o [using](/dotnet/csharp/language-reference/keywords/using-statement) necesarias del código copiado y pegado.

**Cuándo:** Es habitual copiar código de distintos lugares del proyecto u otros orígenes y pegarlo en el nuevo código. Esta acción rápida busca las instrucciones import que faltan en el código copiado y pegado y, luego, le pide que las agregue.

**Por qué:** Dado que la acción rápida agrega automáticamente las importaciones necesarias, no es necesario copiar manualmente las instrucciones `using` que necesita el código.

## <a name="generate-usings-refactoring"></a>Generar refactorización de instrucciones Using

1. Copie el código de un archivo y péguelo en uno nuevo sin incluir las instrucciones `using` necesarias. El error resultante va acompañado de una corrección de código que agrega las instrucciones `using` que faltan.

    > [!NOTE] 
    > Esta sugerencia debe activarse en **Herramientas > Opciones > Editor de texto > C# > Opciones avanzadas > Directivas Using**.

2. Seleccione Ctrl+. para abrir el menú **Acciones rápidas y refactorizaciones**.

    ![Generar instrucciones Using](media/generate-using-codefix.png)

3. Seleccione **using \<su referencia\>;** para agregar la referencia que falta.

    ![Generar resultado de instrucciones Using](media/generate-using-result.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
