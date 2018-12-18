---
title: Estructura DebugStackFrameDescriptor | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641135"
---
# <a name="debugstackframedescriptor-structure"></a>Estructura DebugStackFrameDescriptor
Enumera los marcos de pila y la salida de las combinaciones de varios enumeradores en el mismo subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Miembros  
 `pdsf`  
 El objeto de marco de pila.  
  
 `dwMin`  
 Una representación dependientes del equipo del intervalo de direcciones físicas asociado con este marco de pila inferior.  
  
 `dwLim`  
 Una representación dependientes del equipo de la superior del intervalo de direcciones físicas asociado con este marco de pila.  
  
 `fFinal`  
 Marca que indica que se está procesando el marco.  
  
 `punkFinal`  
 Si este parámetro no es `NULL`, debe detener el enumerador actual combinación y se debe iniciar uno nuevo. El objeto indica cómo iniciar la nueva enumeración.  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de depuración del proceso utiliza esta estructura para ordenar los marcos de pila de varios motores de script. Por convención, las pilas crecen hacia abajo. En consecuencia, en arquitecturas de donde pilas crecen hasta las direcciones deben estar complementan pares.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)