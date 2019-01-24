---
title: THREADPROPERTIES | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 554bc8171de759ce1c79e563bdccf093be31af04
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914710"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Describe las propiedades de un subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```csharp  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## <a name="members"></a>Miembros  
 dwFields  
 Una combinación de marcas de la [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) enumeración, que describe qué campos de esta estructura son válidos.  
  
 dwThreadId  
 El identificador de subproceso.  
  
 dwSuspendCount  
 Recuento de suspensiones el subproceso.  
  
 dwThreadState  
 Un valor de la [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) enumeración que indica el estado del subproceso de funcionamiento.  
  
 bstrPriority  
 Una cadena que especifica la prioridad del subproceso; Por ejemplo, "Anterior" Normal","Normal"o"Tiempo crítico".  
  
 bstName  
 El nombre del subproceso.  
  
 bstrLocation  
 La ubicación del subproceso (normalmente en el marco de pila más alto), normalmente expresada como el nombre del método donde actualmente se detiene la ejecución.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se rellena mediante una llamada a la [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) método. La información devuelta por lo que normalmente se usa para rellenar el **subprocesos** ventana.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)