---
title: 'Cómo: salir de código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2648d73887f79f9b71770164a620bb1a8d674622
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279440"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Cómo: Salir de código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si el código tiene marcos nativos que son invisibles en el **pila de llamadas** ventana, ejecución paso a paso fuera del código administrado puede producir resultados inesperados. Como alternativa, puede usar un punto de interrupción en lugar de **paso a paso fuera**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Para salir de una llamada a código administrado cuando los marcos nativos no se muestran en la pila de llamadas  
  
1.  En el código nativo, establezca un punto de interrupción de ubicación después de la llamada al código administrado.  
  
2.  En el **depurar** menú, elija **continuar**.  
  
     Cuando se complete la llamada administrada, la ejecución se interrumpirá en el punto de interrupción del código nativo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)





