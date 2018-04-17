---
title: 'Cómo: salir de código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5c64016f5ca0613a2986ec8a0bf305d88ecffd64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Cómo: Salir de código administrado cuando los marcos nativos no aparecen en la ventana Pila de llamadas
Si el código tiene marcos nativos que no son visibles en el **pila de llamadas** ventana, salir de código administrado puede generar resultados inesperados. Como alternativa, puede usar un punto de interrupción en lugar de **paso a paso fuera**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Para salir de una llamada a código administrado cuando los marcos nativos no se muestran en la pila de llamadas  
  
1.  En el código nativo, establezca un punto de interrupción de ubicación después de la llamada al código administrado.  
  
2.  En el **depurar** menú, elija **continuar**.  
  
     Cuando se complete la llamada administrada, la ejecución se interrumpirá en el punto de interrupción del código nativo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md)