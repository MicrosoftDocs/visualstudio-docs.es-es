---
title: THUNK_ORDINAL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c74d7d9f419a524ac7ef4c96d304c366f1a7c14
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Designa los tipos de código thunk.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Elementos  
 THUNK_ORDINAL_NOTYPE  
 Código thunk estándar.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Un `this` código thunk de ajustador.  
  
 THUNK_ORDINAL_VCALL  
 Código thunk de llamada virtual.  
  
 THUNK_ORDINAL_PCODE  
 Código thunk de código empaquetado.  
  
 THUNK_ORDINAL_LOAD  
 Código thunk de carga de retraso.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Código thunk de cama elástica incremental (se usa un código thunk cama elástica rebote llamadas de espacio de memoria de uno a otro).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Código thunk cama elástica de punto de bifurcación.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se devuelven desde una llamada a la [idiasymbol:: Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)