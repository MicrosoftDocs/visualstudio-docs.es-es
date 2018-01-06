---
title: BP_LOCATION_CODE_ADDRESS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_CODE_ADDRESS
helpviewer_keywords: BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c7c2378fd9735f097bf0762cf41804862041db9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
Describe la ubicación de un punto de interrupción en una dirección en el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## <a name="members"></a>Miembros  
 `bstrContext`  
 El contexto del punto de interrupción, normalmente un nombre de método o una función como se ve en una pila de llamadas.  
  
 `bstrModuleUrl`  
 La dirección URL del módulo que contiene el punto de interrupción.  
  
 `bstrFunction`  
 El nombre de la función que contiene el punto de interrupción.  
  
 `bstrAddress`  
 La dirección del punto de interrupción, que se analiza mediante un evaluador de expresiones para enlazarlo a un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es un miembro de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estructura como parte de una unión.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)