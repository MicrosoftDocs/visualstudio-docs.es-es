---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f5a0533e2f7ce50dce7ccdf1285e4ab28a4b7a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998505"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa una posición en el espacio de direcciones de la máquina que ejecuta el programa que se está depurando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz para representar una dirección de memoria.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) o [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) devuelve esta interfaz. Además, las llamadas a [agregar](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) y [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) devolver nuevas copias de esta interfaz se haya aplicado la operación aritmética correspondiente.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugMemoryContext2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtiene el nombre de usuario que se puede mostrar para este contexto.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtiene la información que describe este contexto.|  
|[Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Agrega un valor especificado a la dirección del contexto actual para crear un nuevo contexto.|  
|[Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Resta un valor especificado de la dirección del contexto actual para crear un nuevo contexto.|  
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compara dos contextos de la manera indicados por los marcadores de comparación.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio **memoria** ventana llamadas [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) para obtener el `IDebugMemoryContext2` interfaz que contiene la expresión evaluada que se usa para la dirección de memoria. Este contexto, a continuación, se pasa a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) y [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) para especificar la dirección para leer o escribir.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
