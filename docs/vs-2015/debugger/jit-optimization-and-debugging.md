---
title: Optimización y depuración JIT | Microsoft Docs
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
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690533"
---
# <a name="jit-optimization-and-debugging"></a>Optimización y depuración JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al depurar una aplicación administrada, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] suprime de forma predeterminada la optimización del código Just-in-Time (JIT). Suprimir la optimización JIT significa que se está depurando código no optimizado. El código se ejecuta un poco más lentamente porque no se optimiza, pero la experiencia de depuración es mucho más profunda. La depuración de código optimizado es más difícil, y sólo se recomienda si se detecta un error en el código optimizado que no se puede reproducir en la versión no optimizada.  
  
 La optimización JIT se controla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mediante la opción **suprimir optimización JIT al cargar el módulo** . Puede encontrar esta opción en la página **General** , bajo el nodo **depuración** , en el cuadro de diálogo **Opciones** .  
  
 Si desactiva la opción **suprimir optimización JIT al cargar el módulo** , puede depurar el código JIT optimizado, pero su capacidad de depuración puede ser limitada porque el código optimizado no coincide con el código fuente. Como resultado, es posible que las ventanas del depurador como las ventanas **variables locales** y **automático** no muestren tanta información como si se depurara código no optimizado.  
  
 Otra diferencia importante es relativa a la depuración con Sólo mi código. Si se depura con Sólo mi código, el depurador considera que el código optimizado no es del usuario, por lo que no debería mostrarse durante la depuración. Por consiguiente, si depura código optimizado JIT, probablemente desee desactivar Sólo mi código. Para obtener más información, vea  [restringir la ejecución paso a solo mi código](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Recuerde que la opción **suprimir optimización JIT al cargar el módulo** suprime la optimización del código cuando se cargan los módulos. Si se asocia a un proceso que ya se está ejecutando, éste puede contener código que ya esté cargado, con compilación y optimización JIT. La opción **suprimir optimización JIT al cargar el módulo** no tiene ningún efecto en dicho código, aunque afectará a los módulos que se cargan después de la asociación. Además, la opción **suprimir optimización JIT al cargar el módulo** no afecta a los módulos, como WinForms.dll, que se crean con Ngen.  
  
## <a name="see-also"></a>Consulte también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md)   
 [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proceso de ejecución administrada](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
