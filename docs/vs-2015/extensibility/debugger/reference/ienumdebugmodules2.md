---
title: IEnumDebugModules2 | Microsoft Docs
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
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8177463d1eabf222c34fefc09eb7115cd010e97f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266739"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz enumera una lista de módulos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) implementa esta interfaz para representar una lista de los módulos cargados para un programa.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llamadas visuales Studio [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugModules2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera un número especificado de módulos en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Omite un número especificado de módulos en una secuencia de enumeración.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Obtiene el número de módulos.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio usa esta interfaz principalmente para actualizar el **módulos** ventana.  
  
 Para los fines de depuración en Visual Studio, un programa es una secuencia lógica de instrucciones de código que pueden cruzar los límites del módulo, por lo tanto, la necesidad de una lista de módulos para una sola [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz. Normalmente, el primer módulo en la lista contiene el punto de entrada inicial para el programa asociado.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)

