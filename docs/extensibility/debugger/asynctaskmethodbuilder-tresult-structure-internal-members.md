---
title: "Estructura de AsyncTaskMethodBuilder &lt; TResult &gt; - miembros internos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Estructura de AsyncTaskMethodBuilder < TResult > [motores de depuración de .NET Framework]"
  - "motores de depuración, AsyncTaskMethodBuilder < TResult > (estructura) [.NET Framework]"
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Estructura de AsyncTaskMethodBuilder &lt; TResult &gt; - miembros internos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este tema describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> clase. Para obtener información general acerca de esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> tema de referencia.  
  
 **Espacio de nombres:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 No se puede tener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## Miembros internos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[Propiedad ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtiene un objeto que puede utilizarse para identificar de forma exclusiva este generador al depurador.|  
|[campo m\_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Representa el inicializado de forma diferida crea la tarea.|  
  
## Vea también  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Información interna de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)