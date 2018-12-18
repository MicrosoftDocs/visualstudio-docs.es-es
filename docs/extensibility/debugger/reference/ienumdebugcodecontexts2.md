---
title: IEnumDebugCodeContexts2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc6ff9a173bcfbb87606fe493697857d7ec2b323
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122566"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Esta interfaz enumera los contextos de código asociados con la sesión de depuración, o con un determinado programa o documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para representar una lista de contextos de código para una posición de un texto determinado en un programa o una lista de contextos de código para un contexto de documento en particular.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para obtener esta interfaz que representa una lista de contextos de código para una posición de un texto específico en el documento de origen de un programa.  
  
 Llame a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) para obtener esta interfaz que representa una lista de todos los contextos de código en un documento de origen determinado.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugCodeContexts2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera un número especificado de contextos de código en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Omite un número especificado de contextos de código en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[clon](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtiene el número de contextos de código de un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Llamadas visuales Studio [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para rellenar una lista de contextos de código, el usuario puede elegir al establecer la siguiente instrucción o mostrar el desensamblado disponibles para un archivo de código fuente. Varios contextos de código pueden suceder, por ejemplo, cuando hay varias instancias de una plantilla de estilo de C++.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)