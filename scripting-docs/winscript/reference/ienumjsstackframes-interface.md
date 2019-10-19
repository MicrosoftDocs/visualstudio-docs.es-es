---
title: Interfaz IEnumJsStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4a635a802ae84b8e839159f5e2f1c4c461e05ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572031"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames (Interfaz)
Implementado por el depurador para proporcionar el desenredado de la pila a jscript9diag. dll para JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next (Método)](../../winscript/reference/ienumjsstackframes-next-method.md)|Obtiene el número de marcos especificado.|  
|[IEnumJsStackFrames::Reset (Método)](../../winscript/reference/ienumjsstackframes-reset-method.md)|Restablece el marco de pila en la posición anterior al primer elemento.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)