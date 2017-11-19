---
title: "JIT optimización y depuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acf75c0fbf6f5c3cfcf645d288c4e5e2eb2450d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="jit-optimization-and-debugging"></a>Optimización y depuración JIT
Cuando se depura una aplicación administrada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] suprime la optimización del código just-in-time (JIT) de forma predeterminada. Suprimir la optimización JIT significa que se está depurando código no optimizado. El código se ejecuta un poco más lentamente porque no se optimiza, pero la experiencia de depuración es mucho más profunda. La depuración de código optimizado es más difícil, y sólo se recomienda si se detecta un error en el código optimizado que no se puede reproducir en la versión no optimizada.  
  
 La optimización JIT se controla en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] por el **Suprimir optimización JIT cargar el módulo** opción. Puede encontrar esta opción en el **General** página en el **depuración** nodo en el **opciones** cuadro de diálogo.  
  
 Si desactiva la **Suprimir optimización JIT cargar el módulo** opción, puede depurar código JIT optimizado, pero su capacidad de depuración puede ser limitada debido a que el código optimizado no coincide con el código fuente. Como resultado, ventanas del depurador, como la **locales** y **automático** ventana no se muestren tanta información como lo harían si se depurara código no optimizado.  
  
 Otra diferencia importante es relativa a la depuración con Sólo mi código. Si se depura con Sólo mi código, el depurador considera que el código optimizado no es del usuario, por lo que no debería mostrarse durante la depuración. Por consiguiente, si depura código optimizado JIT, probablemente desee desactivar Sólo mi código. Para obtener más información, consulte [restringir la ejecución paso a paso a solo mi código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Recuerde que el **Suprimir optimización JIT cargar el módulo** opción suprime la optimización del código cuando se cargan los módulos. Si se asocia a un proceso que ya se está ejecutando, éste puede contener código que ya esté cargado, con compilación y optimización JIT. El **Suprimir optimización JIT cargar el módulo** opción no tiene ningún efecto en dicho código, pero sí a los módulos que se cargan después de adjuntar. Además, el **Suprimir optimización JIT cargar el módulo** opción no afecta a los módulos, como WinForms.dll, que se crean con NGEN.  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proceso de ejecución administrada](/dotnet/standard/managed-execution-process)