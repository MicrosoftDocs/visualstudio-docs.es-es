---
title: Encapsulado, sangría y alineación de parámetros
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9c17d5c9d6874c836954941e1fccd8ce9d9f2e3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789072"
---
# <a name="wrap-indent-and-align-parameters"></a>Encapsulado, sangría y alineación de parámetros

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** permite encapsular, aplicar sangría y alinear parámetros.

**Cuándo:** si se tiene una llamada o declaración de método con varios parámetros.

**Por qué:** es más fácil leer una larga lista de parámetros cuando están encapsulados o con una sangría según la preferencia del usuario.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en una lista de parámetros.
2. Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Encapsulado, sangría y alineación de parámetros](media/wrap-parameters.png)

3. Presione **ENTRAR** para aceptar la refactorización.

   ![Aplicación de encapsulado, sangría y alineación de parámetros](media/wrap-parameters-completed.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
