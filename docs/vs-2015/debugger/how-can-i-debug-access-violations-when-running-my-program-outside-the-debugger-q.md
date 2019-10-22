---
title: Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7cfdf356d21558f2024cb83e00bdfc930284b1d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164110"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descripción del problema  
 El programa funciona bien en el entorno de Visual Studio, pero cuando se ejecuta de forma independiente en el sistema operativo Windows, produce una infracción de acceso. ¿Cómo se puede depurar este problema?  
  
## <a name="solution"></a>Solución  
 Establezca la opción [Depuración Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md) y ejecute el programa de forma independiente hasta que se produzca la infracción de acceso. A continuación, en el cuadro de diálogo **Infracción de acceso**, se puede hacer clic en **Cancelar** para iniciar el depurador.  
  
 Vea también el artículo Q133174 de Knowledge Base, "How to Locate Where a General Protection (GP) Fault Occurs". Puede encontrar artículos de Knowledge Base en el CD de MSDN Library o buscándolo [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)
