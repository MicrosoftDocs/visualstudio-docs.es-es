---
title: Depuración F# | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cfe65671e0f3d9b3e4702c9f08740c6694286ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734808"
---
# <a name="debugging-f"></a>Depurar F# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La depuración de F# es similar a la depuración de cualquier lenguaje administrado, con algunas excepciones:  
  
-   El **automático** no mostrar ventana F# variables.  
  
-   El modo Editar y Continuar no se admite en F#. Es posible editar código de F# durante una sesión de depuración pero se debería evitar. Dado que los cambios de código no se aplican durante la sesión de depuración, si se realizan cambios en el código de F# durante la depuración, el código fuente no se corresponderá con el código objeto de la depuración.  
  
-   El depurador no reconoce expresiones de F#. Para escribir una expresión en una ventana de depurador o un cuadro de diálogo durante la depuración de F#, se debe convertir la expresión en la sintaxis de C#. Al convertir una expresión de F# en C#, no olvide que C# usa == como operador de comparación de igualdad y que F# utiliza =.  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)



