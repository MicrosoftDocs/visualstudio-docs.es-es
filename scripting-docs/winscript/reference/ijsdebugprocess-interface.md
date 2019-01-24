---
title: IJsDebugProcess (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecdec77a8bcb3c1fb8a1dc64c63b363b4f001fde
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086663"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess (Interfaz)
Proporciona rutinas para inspeccionar y controlar el proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint (Método)](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Establece el punto de interrupción en la posición del documento especificada.|  
|[IJsDebugProcess::CreateStackWalker (Método)](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Método de generador para el rastreador de pila.|  
|[IJsDebugProcess::PerformAsyncBreak (Método)](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Pone el motor de scripts en modo de interrupción, haciendo que se detenga en la siguiente instrucción de script.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)