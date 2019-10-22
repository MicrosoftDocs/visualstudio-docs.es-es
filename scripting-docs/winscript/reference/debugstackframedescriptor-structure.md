---
title: Estructura Debugstackframedescriptor (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576554"
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
 Objeto de marco de pila.  
  
 `dwMin`  
 Representación dependiente del equipo del intervalo inferior de direcciones físicas asociadas a este marco de pila.  
  
 `dwLim`  
 Representación dependiente del equipo del intervalo superior de direcciones físicas asociadas a este marco de pila.  
  
 `fFinal`  
 Marca que indica que el marco se está procesando.  
  
 `punkFinal`  
 Si este parámetro no se `NULL`, se debe detener la combinación del enumerador actual y debe iniciarse uno nuevo. El objeto indica cómo iniciar la nueva enumeración.  
  
## <a name="remarks"></a>Comentarios  
 El administrador de depuración de proceso utiliza esta estructura para ordenar los marcos de pila de varios motores de scripts. Por Convención, las pilas aumentan de tamaño. Por lo tanto, en las arquitecturas en las que las pilas crecen, las direcciones deben ser de dos complementos.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)