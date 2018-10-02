---
title: Depuración de aplicaciones en modo mixto | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- VB
- CSharp
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
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a2fc5fde5d026fd6fbc7e49153fba5cb95a7a0d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578793"
---
# <a name="debugging-mixed-mode-applications"></a>Depurar aplicaciones en modo mixto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [depurar aplicaciones de modo mixto de](https://docs.microsoft.com/visualstudio/debugger/debugging-mixed-mode-applications).  
  
Una aplicación en modo mixto es cualquier aplicación que combine código nativo (C++) y código administrado (como Visual Basic, Visual C# o C++ administrado que se ejecute en Common Language Runtime). La depuración de aplicaciones en modo mixto es un proceso en gran medida transparente en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]; no difiere mucho de la depuración de una aplicación en modo individual. Sin embargo, existen consideraciones especiales.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Habilitar Editar y continuar de C++ en la depuración en modo mixto  
  
-   Para usar Editar y Continuar para C++ en Visual Studio 2013, tiene que revertir al motor de depuración heredado. Consulte [cambiar a modo de compatibilidad administrado en Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) en el blog Microsoft Application Lifecycle Management.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Evaluación de propiedades en aplicaciones en modo mixto  
 En las aplicaciones en modo mixto, la evaluación de propiedades por parte del depurador es una operación costosa. En consecuencia, las operaciones de depuración como la ejecución paso a paso pueden parecer lentas. Para obtener más información, consulte [ejecución paso a paso](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Si se produce un rendimiento muy bajo en la depuración en modo mixto, puede desactivar la evaluación de propiedades en las ventanas del depurador.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### <a name="to-turn-off-property-evaluation"></a>Para desactivar la evaluación de propiedades  
  
1.  En el menú **Herramientas** , elija **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, abra el **depuración** carpeta y seleccione el **General** categoría.  
  
3.  Desactive el **Habilitar evaluación de propiedades y otras llamadas a función implícitas** casilla de verificación.  
  
 Puesto que las pilas de llamadas nativas y las administradas son diferentes, el depurador no siempre proporciona la pila de llamadas competa para el código mixto. Cuando el código nativo llama a código administrado, quizá observe algunas discrepancias. Para obtener más información, consulte [código mixto e información no mostrada en la ventana Pila de llamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)



