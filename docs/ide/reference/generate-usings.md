---
title: Generar instrucciones Using
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para agregar inmediatamente las importaciones necesarias o directivas de uso para el código de copia y pegado.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 38996d1cda52dfe98b6ce9cf24e5adcca6a8b069
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617167"
---
# <a name="add-missing-usings-in-visual-studio"></a>Agregar instrucciones Using que faltan en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Permite agregar inmediatamente las directivas import o [using](/dotnet/csharp/language-reference/keywords/using-directive) necesarias del código copiado y pegado.

**Cuándo:** Es habitual copiar código de distintos lugares del proyecto u otros orígenes y pegarlo en el nuevo código. Esta acción rápida busca las directivas de importaciones que faltan en el código copiado y pegado y, luego, le pide que las agregue. Esta corrección de código también puede agregar referencias de proyecto a proyecto.

**Por qué:** Dado que la acción rápida agrega automáticamente las importaciones necesarias, no es necesario copiar manualmente las directivas `using` que necesita el código.

## <a name="add-missing-usings-refactoring"></a>Agregar refactorización de instrucciones Using que faltan

1. Copie el código de un archivo y péguelo en uno nuevo sin incluir las directivas `using` necesarias. El error resultante va acompañado de una corrección de código que agrega las directivas `using` que faltan.

    > [!NOTE]
    > Esta sugerencia debe activarse en **Herramientas > Opciones > Editor de texto > C# > Opciones avanzadas > Directivas Using**.

2. Seleccione Ctrl+. para abrir el menú **Acciones rápidas y refactorizaciones**.

    ![Generar instrucciones Using](media/generate-using-codefix.png)

3. Seleccione **using \<your reference\>;** para agregar la referencia que falta.

    ![Generar resultado de instrucciones Using](media/generate-using-result.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)
