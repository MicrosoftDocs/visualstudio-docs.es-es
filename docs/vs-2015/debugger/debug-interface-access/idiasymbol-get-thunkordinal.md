---
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 540eb49b215d06127a47df1defc436a0a307aa6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842427"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el tipo de código thunk de una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 enuncia Devuelve un valor de la enumeración de [enumeración THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) que especifica el tipo de código THUNK de una función.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Notas  
 Esta propiedad solo es válida si el símbolo es un valor de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) de `SymTagThunk` .  
  
 Un "thunk" es un fragmento de código que convierte entre un espacio de direcciones de memoria de 32 bits (también conocido como espacio de direcciones plano) y un espacio de direcciones de 16 bits (conocido como espacio de direcciones segmentado).  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
