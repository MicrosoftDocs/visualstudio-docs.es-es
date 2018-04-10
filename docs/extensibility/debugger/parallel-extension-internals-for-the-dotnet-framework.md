---
title: Funcionamiento interno de la extensión en paralelo de .NET Framework | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4cc64270cabb3e30ee3c13a1617222349e7b3677
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Funcionamiento interno de extensión paralelo de .NET Framework
Esta sección describe los tipos internos, métodos, y campos de clases que le ayudarán a implementan a un depurador personalizado para las extensiones paralelas de .NET Framework.  
  
## <a name="in-this-section"></a>En esta sección  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)  
 Se describen los miembros de datos internos de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> clase.  
  
 [Clase de objeto TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Se describen los miembros de datos internos de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> clase.  
  
 [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Se describen los miembros de datos internos de la `System.Threading.Tasks.ContingentProperties` clase.  
  
 [Estructura de AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> estructura.  
  
 [AsyncTaskMethodBuilder\<TResult > estructura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> estructura.  
  
 [Estructura de AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> estructura.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Programación en paralelo](/dotnet/standard/parallel-programming/index)