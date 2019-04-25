---
title: Inversión de expresiones condicionales y operaciones lógicas
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7d59b61cff622a9ba305ebfa86f7c0ebe3c00fe3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157365"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Invertir expresiones condicionales y operadores condicionales AND/OR

Esta refactorización se aplica a lo siguiente:

- C#
- Visual Basic

**Qué:** Permite invertir una expresión condicional o un operador condicional AND/OR.

**Cuándo:** Tiene una expresión condicional o un operador condicional AND/OR que se entendería mejor al invertirse.

**Por qué:** La inversión manual de una expresión o un operador condicional AND/OR puede llevar bastante más tiempo y, posiblemente, dar lugar a errores. Esta corrección de código ayuda a realizar esta refactorización automáticamente.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Invertir refactorización de expresiones condicionales y operadores condicionales AND/OR

1. Coloque el cursor en una expresión condicional o un operador condicional AND/OR.
2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Invertir operador condicional** o **Reemplazar '&&' por '||'**

    ![Invertir operador condicional](media/invert-conditional.png)

    ![Invertir operador condicional](media/invert-logical-operator.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
