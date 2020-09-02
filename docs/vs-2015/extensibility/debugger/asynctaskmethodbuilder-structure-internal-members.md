---
title: 'Estructura AsyncTaskMethodBuilder: miembros internos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bfe640654c9de7daac9096aa4d75f5492a8a278
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555917"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder (Estructura): miembros internos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En este tema se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> clase. Para obtener información general sobre esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> tema de referencia.  
  
 **Espacio de nombres:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no puede tener acceso a estos miembros internos desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Miembros internos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Propiedad Objectidfordebugger (](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtiene un objeto que se puede usar para identificar de forma única este generador en el depurador.|  
|[m_builder campo](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Representa el objeto de generador genérico en el que esta instancia no genérica delega.|  
  
## <a name="see-also"></a>Consulte también  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Datos internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
