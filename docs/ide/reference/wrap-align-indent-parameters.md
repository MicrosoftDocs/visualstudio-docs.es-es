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
ms.openlocfilehash: ccdf29e3a4cda2bf5d527a2b712878c1fbd76197
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037578"
---
# <a name="wrap-indent-and-align-parameters-or-arguments"></a>Encapsulado, sangría y alineación de parámetros o argumentos

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite aplicar encapsulado, sangría y alineación a parámetros o argumentos.

**Cuándo:** Tiene una llamada o declaración de método con varios parámetros o argumentos.

**Por qué:** Es más fácil leer una larga lista de parámetros o argumentos cuando están encapsulados o con una sangría según la preferencia del usuario.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en una lista de parámetros.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Encapsulado, sangría y alineación de parámetros](media/wrap-parameters.png)

3. Presione **ENTRAR** para aceptar la refactorización.

   ![Aplicación de encapsulado, sangría y alineación de parámetros](media/wrap-parameters-completed.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
