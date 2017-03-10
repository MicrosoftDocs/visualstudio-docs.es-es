---
title: Proceso de hospedaje (vshost.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: f96040d6e0a652998cc5603b67afbb564d81a8fd
ms.lasthandoff: 02/22/2017

---
# <a name="hosting-process-vshostexe"></a>Proceso de alojamiento (vshost.exe)
El proceso de hospedaje es una característica de Visual Studio que mejora el rendimiento de depuración, permite la depuración de confianza parcial y la evaluación de expresiones en tiempo de diseño. Los archivos del proceso de hospedaje contienen vshost en el nombre de archivo y se colocan en la carpeta de salida del proyecto. Para obtener más información, consulte [Depuración y proceso de hospedaje](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Los archivos del proceso de hospedaje (.vshost.exe) son para que los use Visual Studio y no deben ejecutarse ni implementarse directamente con la aplicación.  
  
## <a name="improved-debugging-performance"></a>Rendimiento de depuración mejorado  
 El proceso de hospedaje crea un dominio de aplicación y asocia el depurador con la aplicación. Al realizar estas tareas se puede introducir un retraso notable entre el momento en que se inicia la depuración y el momento en que se empieza a ejecutar la aplicación. El proceso de hospedaje ayuda a aumentar el rendimiento al crear el dominio de aplicación y asociar el depurador en segundo plano, y al guardar el estado del depurador y dominio de aplicación entre las ejecuciones de la aplicación. Para obtener más información sobre dominios de aplicación, consulte [Dominios de aplicación](http://msdn.microsoft.com/Library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).  
  
## <a name="partial-trust-debugging"></a>Depuración de confianza parcial  
 Se puede especificar una aplicación como aplicación de confianza parcial en la [página Seguridad](../ide/reference/security-page-project-designer.md) del **Diseñador de proyectos**. Para depurar una aplicación de confianza parcial se requiere una inicialización especial del dominio de aplicación. El proceso de hospedaje controla esta inicialización.  
  
## <a name="design-time-expression-evaluation"></a>Evaluación de expresiones en tiempo de diseño  
 La evaluación de expresiones en tiempo de diseño le permite probar el código de la ventana **Inmediato** sin tener que ejecutar la aplicación. El proceso de hospedaje ejecuta este código durante la evaluación de expresiones en tiempo de diseño. Para obtener más información, consulte [Ventana Inmediato](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Vea también  
 [Depuración y proceso de hospedaje](../debugger/debugging-and-the-hosting-process.md)   
 [Cómo: Deshabilitar el proceso de hospedaje](../ide/how-to-disable-the-hosting-process.md)   
 [Ventana Inmediato](../ide/reference/immediate-window.md)   
 [Dominios de aplicación](http://msdn.microsoft.com/Library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)
