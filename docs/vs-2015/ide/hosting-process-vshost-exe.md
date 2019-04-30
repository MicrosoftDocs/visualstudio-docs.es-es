---
title: Proceso de hospedaje (vshost.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90aa5e77c6541b36619615fc253c55f5d78a6b45
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445707"
---
# <a name="hosting-process-vshostexe"></a>Proceso de alojamiento (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proceso de hospedaje es una característica de Visual Studio que mejora el rendimiento de depuración, permite la depuración de confianza parcial y la evaluación de expresiones en tiempo de diseño. Los archivos del proceso de hospedaje contienen vshost en el nombre de archivo y se colocan en la carpeta de salida del proyecto. Para obtener más información, consulte [Depuración y proceso de hospedaje](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
> Los archivos del proceso de hospedaje (.vshost.exe) son para que los use Visual Studio y no deben ejecutarse ni implementarse directamente con la aplicación.  
  
## <a name="improved-debugging-performance"></a>Rendimiento de depuración mejorado  
 El proceso de hospedaje crea un dominio de aplicación y asocia el depurador con la aplicación. Al realizar estas tareas se puede introducir un retraso notable entre el momento en que se inicia la depuración y el momento en que se empieza a ejecutar la aplicación. El proceso de hospedaje ayuda a aumentar el rendimiento al crear el dominio de aplicación y asociar el depurador en segundo plano, y al guardar el estado del depurador y dominio de aplicación entre las ejecuciones de la aplicación. Para obtener más información sobre dominios de aplicación, consulte [Dominios de aplicación](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).  
  
## <a name="partial-trust-debugging"></a>Depuración de confianza parcial  
 Se puede especificar una aplicación como aplicación de confianza parcial en la [página Seguridad](../ide/reference/security-page-project-designer.md) del **Diseñador de proyectos**. Para depurar una aplicación de confianza parcial se requiere una inicialización especial del dominio de aplicación. El proceso de hospedaje controla esta inicialización.  
  
## <a name="design-time-expression-evaluation"></a>Evaluación de expresiones en tiempo de diseño  
 La evaluación de expresiones en tiempo de diseño le permite probar el código de la ventana **Inmediato** sin tener que ejecutar la aplicación. El proceso de hospedaje ejecuta este código durante la evaluación de expresiones en tiempo de diseño. Para obtener más información, consulte [Ventana Inmediato](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Vea también  
 [Depuración y proceso de hospedaje](../debugger/debugging-and-the-hosting-process.md)   
 [Cómo: Deshabilitar el proceso de hospedaje](../ide/how-to-disable-the-hosting-process.md)   
 [Ventana Inmediato](../ide/reference/immediate-window.md)   
 [Dominios de aplicación](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)
