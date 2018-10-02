---
title: 'Cómo: volver a la función que llamó a MFC cuando está detenido | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9148fb0f3431f7edc0d4b69fdf83ef4b629789f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577276"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Cómo: Volver a la función que llamó a MFC cuando está detenido
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: volver a la función que llama a MFC si detiene](https://docs.microsoft.com/visualstudio/debugger/how-to-get-back-to-the-function-that-called-mfc-if-halted).  
  
NOTA]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si ha usado el **interrumpir** comando el **depurar** menú para detener el programa y ha terminado en MFC, y que el problema está en el código, puede usar la ventana Pila de llamadas para volver a la función. Para obtener más información, consulte [Cómo: utilizar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 A veces el código puede interrumpir el bombeo de mensajes. En ese caso, no hay ningún código de usuario en la pila de llamadas. Para evitar este problema, puede usar los puntos de interrupción (posiblemente con condiciones y recuentos de visitas) en lugar de la **interrumpir** comando. Para obtener más información, consulte [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Para navegar a la función desde la que se llamó a MFC  
  
-   Use la **pila de llamadas** ventana.  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)



