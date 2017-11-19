---
title: Estructura de AsyncVoidMethodBuilder - miembros internos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e2a8b9f7e287ccf8bc63a8d7392cba0d58cb9bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Estructura de AsyncVoidMethodBuilder - miembros internos
En este tema se describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> clase. Para obtener información general acerca de esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> tema de referencia.  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Miembros internos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Propiedad ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtiene un objeto que puede utilizarse para identificar de forma exclusiva este generador para el depurador.|  
|[campo de m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Representa el objeto inicializado de forma diferida utilizado por el depurador para identificar de forma única este generador.|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Datos internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)