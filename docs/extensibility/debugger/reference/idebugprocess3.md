---
title: IDebugProcess3 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21c4dfffe02d2550bccf5b23f264ab8283524aa2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121097"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Esta interfaz representa un proceso en ejecución y sus programas. Esta interfaz existe como un reemplazo para varios métodos de la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz. Proporciona control sobre todos los programas en el proceso.  
  
> [!NOTE]
>  [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), y [paso](../../../extensibility/debugger/reference/idebugprogram2-step.md) métodos están en desuso y ya no debe usarse. Utilice los métodos correspondientes en el `IDebugProcess3` de la interfaz en su lugar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante un proveedor de puerto personalizado para administrar programas como un grupo. Cuando se administran como un grupo de programas, puede controlar su ejecución y establecer un idioma para un evaluador de expresiones. Esta interfaz se debe implementar en el proveedor del puerto.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se llama principalmente por el Administrador de sesión de depuración (SDM) con el fin de interactuar con un grupo de programas identificados en este proceso.  
  
 Llame a [QueryInterface](/cpp/atl/queryinterface) en un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continúa la ejecución de o la ejecución paso a paso a través del proceso.|  
|[Ejecutar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Comienza la ejecución de un proceso.|  
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Pasos reenvían una instrucción o instrucción en el proceso.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Obtiene la razón por la que se inició el proceso para la depuración.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Establece el idioma de hospedaje para que el motor de depuración puede cargar el evaluador de expresiones adecuado.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera el idioma establecido actualmente para este proceso.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Deshabilita Editar y continuar (ENC) para este proceso.<br /><br /> Un proveedor de puerto personalizado no implementa este método (siempre debe devolver `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Obtener el estado ENC para este proceso.<br /><br /> Un proveedor de puerto personalizado no implementa este método (siempre debe devolver `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera una matriz de identificadores únicos para los motores de depuración disponible.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)