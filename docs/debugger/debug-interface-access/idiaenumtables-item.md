---
title: IDiaEnumTables::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 805be4cd9f40bdbdb0f02521a0d946c7121847c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939704"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Recupera una tabla por medio de un índice o nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `index`  
 [in] Índice o nombre de la [IDiaTable](../../debugger/debug-interface-access/idiatable.md) va a recuperar. Si se usa una variante de entero, debe estar en el intervalo de 0 a `count`-1, donde `count` es devuelto por la [Idiaenumtables](../../debugger/debug-interface-access/idiaenumtables-get-count.md) método.  
  
 `table`  
 [out] Devuelve un [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objeto que representa la tabla deseada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica una variante de cadena, la cadena de nombres de una tabla determinada. El nombre debe ser uno de los nombres de tabla como se define en [constantes (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Ejemplo  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Constantes (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)