---
title: 'Idiasymbol:: Get_thunkordinal | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed649ffe02cc27f959bf96b826fc02498beb4acd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31469625"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Recupera el tipo de código thunk de una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve un valor de la [THUNK_ORDINAL (enumeración)](../../debugger/debug-interface-access/thunk-ordinal.md) enumeración que especifica el tipo de código thunk de una función.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es válida únicamente si el símbolo como un [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valo `SymTagThunk`.  
  
 Un "código thunk" es un fragmento de código que realiza la conversión entre un espacio de direcciones de memoria de 32 bits (también conocido como espacio de direcciones sin formato) y un espacio de direcciones de 16 bits (conocido como un espacio de direcciones segmentados).  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK_ORDINAL (enumeración)](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md)