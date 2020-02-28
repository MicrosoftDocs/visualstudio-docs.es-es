---
title: Ajustar, aplicar sangría y alinear refactorizaciones
description: Aprenda a encapsular y alinear cadenas de llamadas a método.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 349f2eeccfea4fea03967929b01114c0de1af155
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529423"
---
# <a name="wrap-indent-and-align-refactorings"></a>Ajustar, aplicar sangría y alinear refactorizaciones

## <a name="wrap-and-align-call-chains"></a>Encapsulado y alineación de cadenas de llamada

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** permite encapsular y alinear cadenas de llamadas a método.

**Cuándo:** tiene una cadena larga que consta de varias llamadas a método en una instrucción.

**Por qué:** es más fácil leer una lista larga cuando sus elementos están encapsulados o con una sangría, según la preferencia del usuario.

### <a name="how-to"></a>Procedimiento

1. Coloque el cursor en cualquiera de las cadenas de llamada.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Encapsular la cadena de llamada** o **Encapsular y alinear la cadena de llamada** para aceptar la refactorización.

   ![Encapsulado y alineación de cadenas de llamada](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Encapsulado, sangría y alineación de parámetros o argumentos

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite aplicar encapsulado, sangría y alineación a parámetros o argumentos.

**Cuándo:** Tiene una llamada o declaración de método con varios parámetros o argumentos.

**Por qué:** Es más fácil leer una larga lista de parámetros o argumentos cuando están encapsulados o con una sangría según la preferencia del usuario.

### <a name="how-to"></a>Procedimiento

1. Coloque el cursor en una lista de parámetros.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Encapsulado, sangría y alineación de parámetros](media/wrap-parameters.png)

3. Seleccione **Ajustar todos los parámetros** para aceptar la refactorización.

## <a name="wrap-binary-expressions"></a>Encapsulado de expresiones binarias.

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** permite encapsular expresiones binarias.

**Cuándo:** tiene una expresión binaria.

**Por qué:** resulta más fácil leer una expresión binaria cuando se encapsula de acuerdo con las preferencias del usuario.

### <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la expresión binaria.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Ajustar la expresión** para aceptar la refactorización.

   ![Encapsulado y alineación de cadenas de llamada](media/wrap-binary-expression.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
