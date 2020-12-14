---
title: Generación de refactorización de parámetros
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para generar de forma automática un parámetro de método.
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
ms.openlocfilehash: 21e209f5be9072390df58e78db34811f886fa9c5
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617154"
---
# <a name="generate-parameter"></a>Generación de parámetros

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** genera automáticamente un parámetro de método.

**Cuándo:** se hace referencia a una variable en un método que no existe en el contexto actual y se recibe un error; puede generar un parámetro como una corrección de código. 

**Por qué:** puede modificar rápidamente una firma de método sin perder el contexto.

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor en el nombre de la variable y presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.
1. Seleccione **Generar parámetro**.

   ![Generación de parámetros](media/generate-parameter.png) 

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
