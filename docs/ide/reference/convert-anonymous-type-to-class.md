---
title: Conversión de un tipo anónimo en clase
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir un tipo anónimo en una clase en Visual Studio.
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
monikerRange: '>= vs-2019'
ms.openlocfilehash: a041c077a41ce6b37d74507723ec1ce0f8c9585c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040790"
---
# <a name="convert-anonymous-type-to-class"></a>Conversión de un tipo anónimo en clase

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** convertir un tipo anónimo en clase.

**Cuándo:** si se tiene un tipo anónimo que se quiere continuar compilando en una clase.

**Por qué:** los tipos anónimos son útiles si solo se usan localmente. A medida que crece el código, es bueno disponer de una manera fácil de promoverlos a una clase.

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor en un tipo anónimo.
2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Conversión de un tipo anónimo en clase](media/convert-anon-to-class.png)

2. Presione **ENTRAR** para aceptar la refactorización.

   ![Aceptación de la conversión de un tipo anónimo en clase](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
