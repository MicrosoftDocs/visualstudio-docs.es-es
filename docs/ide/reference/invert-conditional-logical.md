---
title: Inversión de expresiones condicionales y operaciones lógicas
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para invertir una expresión condicional o un operador AND/OR condicional.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 180e42d5399116df95289e4e5fd0aed1255bf3de
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617388"
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
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Invertir operador condicional** o **Reemplazar '&&' por '||'**

    ![Captura de pantalla de la opción Invertir condicional.](media/invert-conditional.png)

    ![Captura de pantalla de la opción Reemplazar && con ||.](media/invert-logical-operator.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
- [Sugerencias para desarrolladores de .NET](../csharp-developer-productivity.md)
