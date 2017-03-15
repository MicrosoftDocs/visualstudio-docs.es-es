---
title: "C&#243;mo: Retroceder o avanzar en la memoria | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, retroceder página o avanzar página en la memoria"
  - "memoria, retroceder página o avanzar página"
  - "Ventana Desensamblado, ver espacio de memoria"
  - "Ventana Memoria, retroceder página o avanzar página en la memoria"
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# C&#243;mo: Retroceder o avanzar en la memoria
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mientras consulta el contenido de la memoria en una ventana **Memoria** o en la ventana **Desensamblado**, puede utilizar la barra de desplazamiento vertical para moverse hacia arriba o abajo en el espacio de memoria.  
  
### Para retroceder o avanzar en la memoria  
  
1.  Para avanzar \(moverse a una dirección de memoria alta\), haga clic en la barra de desplazamiento vertical debajo del cuadro de desplazamiento.  
  
2.  Para retroceder \(moverse a una dirección de memoria baja\), haga clic en la barra de desplazamiento vertical encima del cuadro de desplazamiento.  
  
 Observará que la barra de desplazamiento vertical funciona de un modo distinto al habitual.  El espacio de direcciones de memoria de un equipo moderno es muy grande, por lo que resultaría muy fácil perderse al arrastrar el cuadro de desplazamiento a una ubicación aleatoria.  Por este motivo, el cuadro de desplazamiento se comporta como un resorte y siempre permanece en el centro de la barra de desplazamiento.  En las aplicaciones en código nativo, puede retroceder o avanzar una página, pero no puede desplazarse libremente por la ventana.  
  
 En las aplicaciones administradas, el desensamblado se limita a una función y el desplazamiento se puede realizar normalmente.  
  
 Verá que las direcciones altas aparecen en la parte inferior de la ventana.  Para ver una dirección alta, debe desplazarse hacia abajo, no hacia arriba.  
  
#### Para desplazarse una instrucción máquina arriba o abajo  
  
-   Haga clic en la flecha situada en la parte superior o inferior de la barra de desplazamiento vertical.  
  
## Vea también  
 [Memoria \(Ventana\)](../debugger/memory-windows.md)   
 [Cómo: Utilizar la ventana Desensamblado](../debugger/how-to-use-the-disassembly-window.md)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)