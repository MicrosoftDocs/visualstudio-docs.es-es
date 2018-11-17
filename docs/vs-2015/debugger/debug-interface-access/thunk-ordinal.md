---
title: THUNK_ORDINAL | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f670656eb1ffe610b81ae8e549e04b6fb8919a62
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733947"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Designa los tipos de código thunk.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
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
 Thunk estándar.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Un `this` código thunk ajustador.  
  
 THUNK_ORDINAL_VCALL  
 Código thunk de llamada virtual.  
  
 THUNK_ORDINAL_PCODE  
 Código thunk de código.  
  
 THUNK_ORDINAL_LOAD  
 Código thunk de carga de retraso.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Código thunk de cama elástica incremental (un código thunk de cama elástica se usa para hacer rebotar la llamadas desde el espacio de memoria de uno a otro).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Código thunk cama elástica de punto de bifurcación.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se devuelven en una llamada a la [Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)



