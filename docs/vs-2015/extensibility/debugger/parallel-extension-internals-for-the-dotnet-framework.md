---
title: Datos internos de extensiones en paralelo de .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a7a0cc60f9398e073bcce59f6e03d62d3bb0820
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999115"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Datos internos de extensiones paralelas para .NET Framework
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta sección describen los tipos internos, métodos y campos de clases que le ayudarán a implementan a un depurador personalizado para las extensiones paralelas para .NET Framework.  
  
## <a name="in-this-section"></a>En esta sección  
 [Clase Task](../../extensibility/debugger/task-class-internal-members.md)  
 Se describen los miembros de datos internos de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> clase.  
  
 [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Se describen los miembros de datos internos de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> clase.  
  
 [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Se describen los miembros de datos internos de la `System.Threading.Tasks.ContingentProperties` clase.  
  
 [Estructura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> estructura.  
  
 [AsyncTaskMethodBuilder\<TResult> Structure](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> estructura.  
  
 [Estructura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> estructura.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Programación en paralelo](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
