---
title: 'Idiasymbol:: Get_targetrelativevirtualaddress | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d17163df16f684da227b50c7d1ac793751440ccb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgettargetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
Recupera la dirección virtual relativa (RVA) de un destino de código thunk.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_targetRelativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve la RVA de un destino de código thunk.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Esta propiedad es válida únicamente si el símbolo como un [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valo `SymTagThunk`.  
  
 Un "código thunk" es un fragmento de código que realiza la conversión entre un espacio de direcciones de memoria de 32 bits (también conocido como espacio de direcciones sin formato) y un espacio de direcciones de 16 bits (conocido como un espacio de direcciones segmentados).  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md)