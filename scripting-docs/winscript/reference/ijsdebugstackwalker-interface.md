---
title: Interfaz IJsDebugStackWalker | Microsoft Docs
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
ms.openlocfilehash: 3b06b8c1f9282c42599c798030440c30450ef6dd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574014"
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
|[IJsDebugStackWalker::GetNext (Método)](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Obtiene el fotograma siguiente.|  
  
## <a name="remarks"></a>Comentarios  
 Los recorridos de pila solo se pueden crear mientras el destino está detenido y no son válidos una vez que el proceso de destino ha continuado de nuevo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)