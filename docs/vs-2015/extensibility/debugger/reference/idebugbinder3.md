---
title: IDebugBinder3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f23c2ad4aeaf911e45b28686584d741e5c4d22f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704138"
---
# <a name="idebugbinder3"></a>IDebugBinder3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz proporciona acceso a los tipos, alias y servicios del visualizador personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un motor de depuración implementa esta interfaz para admitir los alias, los servicios del visualizador personalizado y el acceso a la información de tipo de objeto.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Una interfaz [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obtiene esta interfaz mediante [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden vtable  
 Además de los métodos proporcionados por la interfaz [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , esta interfaz implementa lo siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Recupera un objeto de memoria que representa la memoria a la que está enlazado este objeto.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Recupera la excepción asociada a este objeto (si existe).|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Recupera un alias dado su nombre.|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Recupera una matriz de todos los alias de este objeto,|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Obtiene el número de tipos de argumento asociado a este objeto.|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Recupera una lista de tipos de argumento asociados a este objeto.|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtiene una interfaz a un servicio del visualizador.|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Convierte una ubicación de objeto o una dirección de memoria de 64 bits en un contexto de memoria.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: EE. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces de evaluación de expresiones](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
