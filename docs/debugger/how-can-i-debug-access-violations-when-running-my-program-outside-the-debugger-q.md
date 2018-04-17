---
title: Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f3e4a79ba90f887f11c3fd9a7bddf318ace35cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Cómo depurar las infracciones de acceso cuando se ejecuta un programa fuera del depurador
## <a name="problem-description"></a>Descripción del problema  
 El programa funciona bien en el entorno de Visual Studio, pero cuando se ejecuta de forma independiente en el sistema operativo Windows, produce una infracción de acceso. ¿Cómo se puede depurar este problema?  
  
## <a name="solution"></a>Soluciones  
 Establecer el [Just-in-time depuración](../debugger/just-in-time-debugging-in-visual-studio.md) opción y ejecutar el programa de forma independiente hasta que se produce la infracción de acceso. A continuación, en la **infracción de acceso** cuadro de diálogo, puede hacer clic en **cancelar** para iniciar el depurador.  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)