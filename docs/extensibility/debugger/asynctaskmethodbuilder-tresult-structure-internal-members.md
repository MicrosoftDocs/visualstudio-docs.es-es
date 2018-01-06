---
title: AsyncTaskMethodBuilder&lt;TResult&gt; estructura - miembros internos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 504a958507fce69e5bb3b65ea9f669dc9a8acba4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; estructura - miembros internos
En este tema se describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> clase. Para obtener información general acerca de esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> tema de referencia.  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Miembros internos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Propiedad ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtiene un objeto que puede utilizarse para identificar de forma exclusiva este generador para el depurador.|  
|[campo de m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Representa el inicializado de forma diferida genera la tarea.|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Datos internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)