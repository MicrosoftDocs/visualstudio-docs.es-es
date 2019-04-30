---
title: IJsDebugStackWalker (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d06af2c509339d9499f66e1f267c54c69951e225
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977817"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker (Interfaz)
Representa un rastreador de pila para un subproceso especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext (Método)](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Obtiene el siguiente fotograma.|  
  
## <a name="remarks"></a>Comentarios  
 Solo se pueden crear rastreadores de pila, mientras que el destino se ha detenido y no son válido una vez que se ha seguido el proceso de destino.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)