---
title: IJsDebugStackWalker (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbea11bf1188d148818ea8a082bceec76c704c2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728555"
---
# <a name="ijsdebugstackwalker-interface"></a>IJsDebugStackWalker (Interfaz)
Representa un rastreador de pila para un subproceso especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext (Método)](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Obtiene el siguiente fotograma.|  
  
## <a name="remarks"></a>Comentarios  
 Andadores de pila solo pueden crearse mientras el destino se ha detenido y no son válido una vez que el proceso de destino se ha ido de nuevo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)