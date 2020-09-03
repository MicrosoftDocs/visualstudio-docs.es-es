---
title: 'Estructura AsyncVoidMethodBuilder: miembros internos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 770e66c4136379a24cee349b04fcc06f5278a379
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201097"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder (Estructura): miembros internos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En este tema se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> clase. Para obtener información general sobre esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> tema de referencia.  
  
 **Espacio de nombres:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no puede tener acceso a estos miembros internos desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Miembros internos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Propiedad Objectidfordebugger (](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtiene un objeto que se puede usar para identificar de forma única este generador en el depurador.|  
|[m_objectIdForDebugger campo](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Representa el objeto inicializado de forma diferida que usa el depurador para identificar de forma exclusiva a este generador.|  
  
## <a name="see-also"></a>Consulte también  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Datos internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
