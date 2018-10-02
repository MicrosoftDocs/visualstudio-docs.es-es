---
title: Datos internos de extensiones en paralelo de .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16ce4309cc8951d068b3d048e6bfac9ae863cd89
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574312"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Datos internos de extensiones paralelas para .NET Framework
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [datos internos de extensiones paralelas para .NET Framework](https://docs.microsoft.com/visualstudio/extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework).  
  
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
  
 [AsyncTaskMethodBuilder\<TResult > estructura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> estructura.  
  
 [Estructura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> estructura.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Programación en paralelo](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)

