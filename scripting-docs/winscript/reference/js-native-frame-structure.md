---
title: Estructura JS_NATIVE_FRAME | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_NATIVE_FRAME
apilocation:
- jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7e93041a6dec767cb3bb11382abfb562068c925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733845"
---
# <a name="jsnativeframe-structure"></a>Estructura JS_NATIVE_FRAME
Representa un marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>Miembros  
 `InstructionOffset`  
 Puntero de instrucción.  
  
 `ReturnOffset`  
 Dirección de devolución.  
  
 `FrameOffset`  
 Puntero de marco.  
  
 `StackOffset`  
 Puntero de pila.  
  
## <a name="remarks"></a>Comentarios  
 `JS_NATIVE_FRAME` utiliza el struct `IJsStackFrameEnumerator`.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)