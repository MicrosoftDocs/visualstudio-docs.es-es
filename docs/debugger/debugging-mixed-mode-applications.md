---
title: "Depuración de aplicaciones en modo mixto | Documentos de Microsoft"
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
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ee3e5401b663435415c0f3004054090be82e916
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-mixed-mode-applications"></a>Depurar aplicaciones en modo mixto
Una aplicación en modo mixto es cualquier aplicación que combine código nativo (C++) y código administrado (como Visual Basic, Visual C# o C++ administrado que se ejecute en Common Language Runtime). La depuración de aplicaciones en modo mixto es un proceso en gran medida transparente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; no difiere mucho de la depuración de una aplicación en modo individual. Sin embargo, existen consideraciones especiales.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Habilitar Editar y continuar de C++ en la depuración en modo mixto  
  
-   Para usar Editar y Continuar para C++ en Visual Studio 2013, tiene que revertir al motor de depuración heredado. Vea [cambiar al modo de compatibilidad administrada de Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) en el blog de Microsoft Application Lifecycle Management.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Evaluación de propiedades en aplicaciones en modo mixto  
 En las aplicaciones en modo mixto, la evaluación de propiedades por parte del depurador es una operación costosa. En consecuencia, las operaciones de depuración como la ejecución paso a paso pueden parecer lentas. Para obtener más información, consulte [depurar paso a paso](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Si se produce un rendimiento muy bajo en la depuración en modo mixto, puede desactivar la evaluación de propiedades en las ventanas del depurador.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
#### <a name="to-turn-off-property-evaluation"></a>Para desactivar la evaluación de propiedades  
  
1.  En el menú **Herramientas** , elija **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, abra el **depuración** carpeta y seleccione la **General** categoría.  
  
3.  Desactive el **Habilitar evaluación de propiedades y otras llamadas a función implícitas** casilla de verificación.  
  
 Puesto que las pilas de llamadas nativas y las administradas son diferentes, el depurador no siempre proporciona la pila de llamadas competa para el código mixto. Cuando el código nativo llama a código administrado, quizá observe algunas discrepancias. Para obtener más información, consulte [código mixto e información no mostrada en la ventana Pila de llamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)