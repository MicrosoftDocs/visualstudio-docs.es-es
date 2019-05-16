---
title: IDebugProgramHost2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2bcb65872f9f451e1cc4e5030532e0a444af1139
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687782"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz proporciona información de host (proceso) acerca de un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración implementa esta interfaz en el mismo objeto que el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz para proporcionar información sobre el proceso de hospedaje. Se trata de una interfaz opcional.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en un `IDebugProgram2` interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProgramHost2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Obtiene el título, el nombre descriptivo o el nombre de archivo del proceso de hospedaje de este programa.|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Obtiene el identificador de proceso del proceso de hospedaje de este programa.|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Obtiene el nombre de la máquina en que se está ejecutando el proceso de hospedaje de este programa.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
