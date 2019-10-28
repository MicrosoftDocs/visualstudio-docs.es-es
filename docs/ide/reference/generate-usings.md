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
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 78786e6e6e7a8e5d8a8766138cb1a54a49416f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610889"
---
# <a name="add-missing-usings-in-visual-studio"></a>Agregar instrucciones Using que faltan en Visual Studio

Esta generación de código se aplica a:

- C#

**Qué:** Permite agregar inmediatamente las directivas import o [using](/dotnet/csharp/language-reference/keywords/using-directive) necesarias del código copiado y pegado.

**Cuándo:** Es habitual copiar código de distintos lugares del proyecto u otros orígenes y pegarlo en el nuevo código. Esta acción rápida busca las directivas de importaciones que faltan en el código copiado y pegado y, luego, le pide que las agregue.

**Por qué:** Dado que la acción rápida agrega automáticamente las importaciones necesarias, no es necesario copiar manualmente las directivas `using` que necesita el código.

## <a name="add-missing-usings-refactoring"></a>Agregar refactorización de instrucciones Using que faltan

1. Copie el código de un archivo y péguelo en uno nuevo sin incluir las directivas `using` necesarias. El error resultante va acompañado de una corrección de código que agrega las directivas `using` que faltan.

    > [!NOTE]
    > Esta sugerencia debe activarse en **Herramientas > Opciones > Editor de texto > C# > Opciones avanzadas > Directivas Using**.

2. Seleccione Ctrl+. para abrir el menú **Acciones rápidas y refactorizaciones**.

    ![Generar instrucciones Using](media/generate-using-codefix.png)

3. Seleccione **using \<su referencia\>;** para agregar la referencia que falta.

    ![Generar resultado de instrucciones Using](media/generate-using-result.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)
