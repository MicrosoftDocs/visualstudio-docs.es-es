---
title: IDebugProviderProgramNode2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProviderProgramNode2
helpviewer_keywords: IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8c083d9b054ecde18d1e1fff8ca5bb8cbb6be659
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Esta interfaz calcula las referencias de interfaces relacionadas con el programa a través de límites de proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz en el mismo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para admitir la serialización de interfaces en los límites del proceso.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [QueryInterface](/cpp/atl/queryinterface) en un `IDebugProgramNode2` interfaz para obtener esta interfaz. Si no se puede obtener esta interfaz, la DE no admite la serialización de interfaces.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtiene una interfaz especificada a través de los límites del proceso.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se implementa cuando el Alemania se ejecuta en un espacio de proceso independiente desde el programa que se está depurando: por ejemplo, cuando se ejecuta la DE en el espacio de proceso de Visual Studio en lugar del espacio de proceso del programa que se está depurando.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)