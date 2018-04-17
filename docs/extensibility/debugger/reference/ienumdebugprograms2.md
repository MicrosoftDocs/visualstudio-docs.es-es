---
title: IEnumDebugPrograms2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1e95996a0548dcf81957dad60c3e6f73b3424c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Esta interfaz enumera los programas que se ejecutan en la sesión de depuración actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para proporcionar una lista de programas que se está depurando con la DE.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llamadas visuales Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) para obtener esta interfaz. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) no se utiliza Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugPrograms2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera un número especificado de programas en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Omite un número especificado de programas en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[clon](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtiene el número de programas de un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio usa esta interfaz para:  
  
-   Rellenar el **módulos** ventana (mediante una llamada a [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) y, a continuación, llamar a [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) en cada programa).  
  
-   Rellenar el **adjuntar al proceso** lista (mediante una llamada a `IDebugProcess2::EnumPrograms` y, a continuación, llamar a [QueryInterface](/cpp/atl/queryinterface) en cada [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz para obtener un [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interfaz).  
  
-   Generar una lista de DEs que puede depurar cada programa en el proceso (mediante [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Aplicar actualizaciones de editar y continuar (ENC) para cada programa (llamando IDebugProcess2::EnumPrograms y, a continuación, llame a [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)