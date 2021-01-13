---
title: Ajustar, aplicar sangría y alinear refactorizaciones
description: Aprenda a encapsular y alinear cadenas de llamadas a método.
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
ms.openlocfilehash: d8a98ebd1fa1e8a9ec937cf4e0965d804a8a9387
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761230"
---
# <a name="wrap-indent-and-align-refactorings"></a>Ajustar, aplicar sangría y alinear refactorizaciones

## <a name="wrap-and-align-call-chains"></a>Encapsulado y alineación de cadenas de llamada

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** permite encapsular y alinear cadenas de llamadas a método.

**Cuándo:** tiene una cadena larga que consta de varias llamadas a método en una instrucción.

**Por qué:** es más fácil leer una lista larga cuando sus elementos están encapsulados o con una sangría, según la preferencia del usuario.

### <a name="how-to"></a>Procedimiento

1. Coloque el cursor en cualquiera de las cadenas de llamada.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Encapsular la cadena de llamada** o **Encapsular y alinear la cadena de llamada** para aceptar la refactorización.

   ![Captura de pantalla en la que se muestran el menú Acciones rápidas y refactorizaciones de Visual Studio con la opción Encapsular la cadena de llamada seleccionada, y cambios en el código de C#.](media/wrap-call-chain.png)

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

- Visual Basic

**Qué:** permite encapsular expresiones binarias.

**Cuándo:** tiene una expresión binaria.

**Por qué:** resulta más fácil leer una expresión binaria cuando se encapsula de acuerdo con las preferencias del usuario.

### <a name="how-to"></a>Procedimiento

1. Coloque el cursor en la expresión binaria.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
3. Seleccione **Ajustar la expresión** para aceptar la refactorización.

   ![Captura de pantalla en la que se muestran el menú Acciones rápidas y refactorizaciones de Visual Studio con la opción Ajustar la expresión seleccionada, y cambios en el código de C#.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
