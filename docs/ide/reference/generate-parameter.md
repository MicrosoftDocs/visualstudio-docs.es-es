---
title: Generación de refactorización de parámetros
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e95e76c35afdb8cdbe38c8b33329734ba68361b1
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329053"
---
# <a name="generate-parameter"></a>Generación de parámetros

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** genera automáticamente un parámetro de método.

**Cuándo:** se hace referencia a una variable en un método que no existe en el contexto actual y se recibe un error; puede generar un parámetro como una corrección de código. 

**Por qué:** puede modificar rápidamente una firma de método sin perder el contexto.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor en el nombre de la variable y presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
1. Seleccione **Generar parámetro**.

   ![Generación de parámetros](media/generate-parameter.png) 

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
