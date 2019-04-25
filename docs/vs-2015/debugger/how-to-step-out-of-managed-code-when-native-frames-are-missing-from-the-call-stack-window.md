---
title: Procedimiento Salir de código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 684738fd2180a3c5bf269b2a30efd970bcf9ab08
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092206"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Procedimiento Salida del código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si el código tiene marcos nativos que no se ven en la ventana **Pila de llamadas**, salir de código administrado puede generar resultados inesperados. Como solución, puede utilizar un punto de interrupción en lugar de **Paso a paso para salir**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Para salir de una llamada a código administrado cuando los marcos nativos no se muestran en la pila de llamadas  
  
1. En el código nativo, establezca un punto de interrupción de ubicación después de la llamada al código administrado.  
  
2. En el menú **Depurar**, elija **Continuar**.  
  
     Cuando se complete la llamada administrada, la ejecución se interrumpirá en el punto de interrupción del código nativo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)
