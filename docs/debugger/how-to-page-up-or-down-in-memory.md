---
title: 'Cómo: retroceder o avanzar en la memoria | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25c057687596e5f410c4a19f9a1c8c2cdef02f28
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816662"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Cómo: Retroceder o avanzar en la memoria
Al ver el contenido de la memoria en un **memoria** ventana o el **desensamblado** ventana, puede usar la barra de desplazamiento vertical para moverse hacia arriba o hacia abajo en el espacio de memoria.  
  
### <a name="to-page-up-or-down-in-memory"></a>Para retroceder o avanzar en la memoria  
  
1. Para avanzar (moverse a una dirección de memoria alta), haga clic en la barra de desplazamiento vertical debajo del cuadro de desplazamiento.  
  
2. Para retroceder (moverse a una dirección de memoria baja), haga clic en la barra de desplazamiento vertical encima del cuadro de desplazamiento.  
  
   Observará que la barra de desplazamiento vertical funciona de un modo distinto al habitual. El espacio de direcciones de memoria de un equipo moderno es muy grande, por lo que resultaría muy fácil perderse al arrastrar el cuadro de desplazamiento a una ubicación aleatoria. Por este motivo, el cuadro de desplazamiento se comporta como un resorte y siempre permanece en el centro de la barra de desplazamiento. En las aplicaciones en código nativo, puede retroceder o avanzar una página, pero no puede desplazarse libremente por la ventana.  
  
   En las aplicaciones administradas, el desensamblado se limita a una función y el desplazamiento se puede realizar normalmente.  
  
   Verá que las direcciones altas aparecen en la parte inferior de la ventana. Para ver una dirección alta, debe desplazarse hacia abajo, no hacia arriba.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>Para desplazarse una instrucción máquina arriba o abajo  
  
-   Haga clic en la flecha situada en la parte superior o inferior de la barra de desplazamiento vertical.  
  
## <a name="see-also"></a>Vea también  
 [Windows de memoria](../debugger/memory-windows.md)   
 [Cómo: usar la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)