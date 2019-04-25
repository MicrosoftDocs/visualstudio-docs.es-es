---
title: JIT optimización y depuración | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4a0cf53dcc9870b5d0c93d2fcaaf2d942fd9959
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989236"
---
# <a name="jit-optimization-and-debugging"></a>Optimización y depuración JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se depura una aplicación administrada, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] suprime la optimización del código just-in-time (JIT) de forma predeterminada. Suprimir la optimización JIT significa que se está depurando código no optimizado. El código se ejecuta un poco más lentamente porque no se optimiza, pero la experiencia de depuración es mucho más profunda. La depuración de código optimizado es más difícil, y sólo se recomienda si se detecta un error en el código optimizado que no se puede reproducir en la versión no optimizada.  
  
 La optimización JIT se controla en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] por la **Suprimir optimización JIT cargar el módulo** opción. Puede encontrar esta opción en el **General** página bajo la **depuración** nodo en el **opciones** cuadro de diálogo.  
  
 Si desactiva la **Suprimir optimización JIT cargar el módulo** opción, puede depurar código JIT optimizado, pero su capacidad para depurar puede ser limitada debido a que el código optimizado no coincide con el código fuente. Como resultado, ventanas del depurador, como la **variables locales** y **automático** ventana no se muestren tanta información como lo harían si se depurara código no optimizado.  
  
 Otra diferencia importante es relativa a la depuración con Sólo mi código. Si se depura con Sólo mi código, el depurador considera que el código optimizado no es del usuario, por lo que no debería mostrarse durante la depuración. Por consiguiente, si depura código optimizado JIT, probablemente desee desactivar Sólo mi código. Para obtener más información, consulte [restringir la ejecución paso a paso a solo mi código](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Recuerde que el **Suprimir optimización JIT cargar el módulo** opción suprime la optimización del código cuando se cargan los módulos. Si se asocia a un proceso que ya se está ejecutando, éste puede contener código que ya esté cargado, con compilación y optimización JIT. El **Suprimir optimización JIT cargar el módulo** opción no tiene ningún efecto en dicho código, pero sí a los módulos que se cargan después de adjuntar. Además, el **Suprimir optimización JIT cargar el módulo** opción no afecta a los módulos, como WinForms.dll, que se crean con NGEN.  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proceso de ejecución administrada](http://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
