---
title: IEnumJsStackFrames (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12583f73c9f3977371ebd193716f2513fc0befc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames (Interfaz)
Implementado por el depurador para proporcionar la pila desenredar hasta jscript9diag.dll para JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next (Método)](../../winscript/reference/ienumjsstackframes-next-method.md)|Obtiene el número especificado de fotogramas.|  
|[IEnumJsStackFrames::Reset (Método)](../../winscript/reference/ienumjsstackframes-reset-method.md)|Restablece el marco de pila a la posición anterior al primer elemento.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)