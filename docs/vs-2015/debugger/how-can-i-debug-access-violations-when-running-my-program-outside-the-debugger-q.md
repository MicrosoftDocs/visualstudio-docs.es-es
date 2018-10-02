---
title: Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador | Microsoft Docs
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
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1525061210c6ef7cdda32c6204648c3944f4b889
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566912"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [¿How Can I Debug acceso infracciones cuando ejecuta mi programa fuera el depurador?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger-q).  
  
Descripción del problema  
 El programa funciona bien en el entorno de Visual Studio, pero cuando se ejecuta de forma independiente en el sistema operativo Windows, produce una infracción de acceso. ¿Cómo se puede depurar este problema?  
  
## <a name="solution"></a>Soluciones  
 Establecer el [Just-in-time depuración](../debugger/just-in-time-debugging-in-visual-studio.md) opción y ejecutar el programa de forma independiente hasta que se produzca la infracción de acceso. A continuación, en el **infracción de acceso** cuadro de diálogo, puede hacer clic en **cancelar** para iniciar el depurador.  
  
 Vea también el artículo Q133174 de Knowledge Base, "How to Locate Where a General Protection (GP) Fault Occurs". Puede encontrar artículos de Knowledge Base en el CD de MSDN Library o buscándolo [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)



