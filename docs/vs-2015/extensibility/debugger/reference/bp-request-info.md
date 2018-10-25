---
title: BP_REQUEST_INFO | Microsoft Docs
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
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 980bc344949cc3c3acd9bc0bd18170785c09529c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940715"
---
# <a name="bprequestinfo"></a>BP_REQUEST_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contiene la información necesaria para implementar un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```csharp  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## <a name="members"></a>Miembros  
 `dwFields`  
 Una combinación de marcas de la [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumeración que especifica qué campos se rellenan.  
  
 `guidLanguage`  
 GUID de lenguaje.  
  
 `bpLocation`  
 El [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estructura que especifica el tipo de la ubicación del punto de interrupción.  
  
 `pProgram`  
 El [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa la aplicación en el que se produce el punto de interrupción.  
  
 `bstrProgramName`  
 El nombre de la aplicación en el que se produce el punto de interrupción.  
  
 `pThread`  
 El [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso en el que se produce el punto de interrupción.  
  
 `bstrThreadName`  
 El nombre del subproceso en el que se produce el punto de interrupción.  
  
 `bpCondition`  
 El [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) estructura que describe las condiciones en las que se activará el punto de interrupción.  
  
 `bpPassCount`  
 El [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estructura que contiene la información del recuento pase del punto de interrupción.  
  
 `dwFlags`  
 Una combinación de marcas de la [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) enumeración que especifica las marcas para el punto de interrupción solicitado.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es devuelto por la [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) método.  
  
 Si necesita obtener el GUID de proveedor de motor de depuración, la restricción de punto de interrupción o el punto de seguimiento, consulte el [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructura.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

