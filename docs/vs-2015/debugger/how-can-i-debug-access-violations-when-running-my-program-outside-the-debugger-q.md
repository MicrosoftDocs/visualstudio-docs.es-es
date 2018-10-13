---
title: Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 486b981311d93a93866622ccf80b6eabdee748ff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290763"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descripción del problema  
 El programa funciona bien en el entorno de Visual Studio, pero cuando se ejecuta de forma independiente en el sistema operativo Windows, produce una infracción de acceso. ¿Cómo se puede depurar este problema?  
  
## <a name="solution"></a>Soluciones  
 Establecer el [Just-in-time depuración](../debugger/just-in-time-debugging-in-visual-studio.md) opción y ejecutar el programa de forma independiente hasta que se produzca la infracción de acceso. A continuación, en el **infracción de acceso** cuadro de diálogo, puede hacer clic en **cancelar** para iniciar el depurador.  
  
 Vea también el artículo Q133174 de Knowledge Base, "How to Locate Where a General Protection (GP) Fault Occurs". Puede encontrar artículos de Knowledge Base en el CD de MSDN Library o buscándolo [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)



