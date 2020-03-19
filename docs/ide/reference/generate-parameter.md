---
title: Generación de refactorización de parámetros
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
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094355"
---
# <a name="generate-parameter"></a>Generación de parámetros

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** genera automáticamente un parámetro de método.

**Cuándo:** se hace referencia a una variable en un método que no existe en el contexto actual y se recibe un error; puede generar un parámetro como una corrección de código. 

**Por qué:** puede modificar rápidamente una firma de método sin perder el contexto.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en el nombre de la variable y presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
1. Seleccione **Generar parámetro**.

   ![Generación de parámetros](media/generate-parameter.png) 

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
