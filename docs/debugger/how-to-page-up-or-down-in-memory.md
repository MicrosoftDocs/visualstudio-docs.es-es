---
title: 'Cómo: retroceder o avanzar en la memoria | Documentos de Microsoft'
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
ms.openlocfilehash: 5c87dc65bd48d47e54c4c46099c264a0c7051957
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-page-up-or-down-in-memory"></a>Cómo: Retroceder o avanzar en la memoria
Al ver el contenido de la memoria en un **memoria** ventana o el **desensamblado** ventana, puede usar la barra de desplazamiento vertical para moverse hacia arriba o hacia abajo en el espacio de memoria.  
  
### <a name="to-page-up-or-down-in-memory"></a>Para retroceder o avanzar en la memoria  
  
1.  Para avanzar (moverse a una dirección de memoria alta), haga clic en la barra de desplazamiento vertical debajo del cuadro de desplazamiento.  
  
2.  Para retroceder (moverse a una dirección de memoria baja), haga clic en la barra de desplazamiento vertical encima del cuadro de desplazamiento.  
  
 Observará que la barra de desplazamiento vertical funciona de un modo distinto al habitual. El espacio de direcciones de memoria de un equipo moderno es muy grande, por lo que resultaría muy fácil perderse al arrastrar el cuadro de desplazamiento a una ubicación aleatoria. Por este motivo, el cuadro de desplazamiento se comporta como un resorte y siempre permanece en el centro de la barra de desplazamiento. En las aplicaciones en código nativo, puede retroceder o avanzar una página, pero no puede desplazarse libremente por la ventana.  
  
 En las aplicaciones administradas, el desensamblado se limita a una función y el desplazamiento se puede realizar normalmente.  
  
 Verá que las direcciones altas aparecen en la parte inferior de la ventana. Para ver una dirección alta, debe desplazarse hacia abajo, no hacia arriba.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>Para desplazarse una instrucción máquina arriba o abajo  
  
-   Haga clic en la flecha situada en la parte superior o inferior de la barra de desplazamiento vertical.  
  
## <a name="see-also"></a>Vea también  
 [Memoria (ventana)](../debugger/memory-windows.md)   
 [Cómo: utilizar la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)