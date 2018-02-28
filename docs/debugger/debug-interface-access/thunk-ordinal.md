---
title: THUNK_ORDINAL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0911b01bf52bd73cd438be024dab2580c5a94d1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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