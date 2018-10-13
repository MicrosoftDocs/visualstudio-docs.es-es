---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbb01738876eb342fecb83f7f6d09c850ee89636
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247642"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz enumera los programas que se ejecutan en la sesión de depuración actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz para proporcionar una lista de programas que se está depurando por la DE.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llamadas visuales Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) para obtener esta interfaz. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) no se usa Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugPrograms2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera un número especificado de programas en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Omite un número especificado de programas en una secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtiene el número de programas en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio usa esta interfaz para:  
  
-   Rellenar el **módulos** ventana (mediante una llamada a [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) y, a continuación, llamar a [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) en cada programa).  
  
-   Rellenar el **asociar al proceso** lista (mediante una llamada a `IDebugProcess2::EnumPrograms` y, a continuación, llamar a [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en cada [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz para obtener un [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interfaz).  
  
-   Generar una lista de DEs que puede depurar cada programa en el proceso (mediante [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Aplicar actualizaciones de editar y continuar (ENC) para cada programa (llamando IDebugProcess2::EnumPrograms y, a continuación, llame a [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

