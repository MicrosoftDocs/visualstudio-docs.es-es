---
title: DebugStackFrameDescriptor (estructura) | Documentos de Microsoft
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
ms.openlocfilehash: c50c717cad626f4caf634c6a83b2af7213b78f83
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088483"
---
# <a name="debugstackframedescriptor-structure"></a>Estructura DebugStackFrameDescriptor
Enumera los marcos de pila y la salida de las combinaciones de varios enumeradores en el mismo subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 Una representación de dependiente de la máquina del intervalo de direcciones físicas asociado con este marco de pila inferior.  
  
 `dwLim`  
 Una representación de dependiente de la máquina de la superior del intervalo de direcciones físicas asociado con este marco de pila.  
  
 `fFinal`  
 Marca que indica que se está procesando el marco.  
  
 `punkFinal`  
 Si este parámetro no es `NULL`, debe detener el enumerador actual de combinación y se debe iniciar una nueva. El objeto indica cómo iniciar la nueva enumeración.  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de depuración de procesos utiliza esta estructura para ordenar los marcos de pila de varios motores de script. Por convención, las pilas crecen de abajo. Por lo tanto, en las arquitecturas que crecen pilas, las direcciones deben ser complementado por dos.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)