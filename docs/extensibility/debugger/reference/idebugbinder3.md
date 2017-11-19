---
title: IDebugBinder3 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3
helpviewer_keywords: IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 437d8414c725ffe7f5dab992da262de918c03693
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz proporciona acceso a tipos, alias y servicios de visualizador personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un motor de depuración implementa esta interfaz para admitir el alias, servicios de visualizador personalizado y acceso a la información de tipo de objeto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaz obtiene esta interfaz mediante [QueryInterface](/cpp/atl/queryinterface).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos proporcionados por el [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaz, esta interfaz implementa lo siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Recupera un objeto de memoria que representa la memoria a la que está enlazado este objeto.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Recupera la excepción asociada a este objeto (si existe),|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Recupera un alias dado su nombre,|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Recupera una matriz de todos los alias para este objeto|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Obtiene el número de tipos de argumentos asociada a este objeto|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Recupera una lista de tipos de argumentos asociada a este objeto|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtiene una interfaz a un servicio del visualizador,|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Convierte una ubicación del objeto o una dirección de memoria de 64 bits en un contexto de la memoria.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)