---
title: IJsDebugFrame (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f09a147375661fb52b88f531aff981897138adff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame (Interfaz)
Representa un marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IJsDebugFrame::Evaluate (Método)](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Evalúa una expresión en el contexto de este marco de pila.|  
|[IJsDebugFrame::GetDebugProperty (Método)](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Devuelve un explorador de propiedades para este marco de pila.|  
|[IJsDebugFrame::GetDocumentPositionWithId (Método)](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Devuelve la posición actual de este marco de pila dentro del documento de nivel de usuario.|  
|[IJsDebugFrame::GetDocumentPositionWithName (Método)](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Devuelve la posición actual de este marco de pila dentro del documento de nivel de usuario.|  
|[IJsDebugFrame::GetName (Método)](../../winscript/reference/ijsdebugframe-getname-method.md)|Obtiene el nombre descriptivo del marco de pila.|  
|[IJsDebugFrame::GetReturnAddress (Método)](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Obtiene la dirección de devolución insertada en el 'inicio' (vea GetStackRange) del marco.|  
|[IJsDebugFrame::GetStackRange (Método)](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Devuelve el intervalo de direcciones absolutas del marco de pila de JavaScript lógico.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)