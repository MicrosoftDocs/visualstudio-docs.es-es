---
title: 'AsyncVoidMethodBuilder Structure: miembros internos | Microsoft Docs'
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
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 408e3028c09c6c96af2a43977dc0c8cd720b70c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578449"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder (Estructura): miembros internos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [AsyncVoidMethodBuilder Structure: miembros internos](https://docs.microsoft.com/visualstudio/extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members).  
  
En este tema se describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> clase. Para obtener información general acerca de esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> tema de referencia.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Miembros internos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Propiedad ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtiene un objeto que puede utilizarse para identificar de forma única este generador para el depurador.|  
|[campo m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Representa el objeto inicializado de forma diferida utilizado por el depurador para identificar de forma única este generador.|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Datos internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

