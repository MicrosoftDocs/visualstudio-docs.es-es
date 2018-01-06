---
title: 'Idiaenumtables:: Item | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fd0049e15f17d5dff58d35d4279bb0ab0673091e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 [in] Índice o nombre de la [IDiaTable](../../debugger/debug-interface-access/idiatable.md) va a recuperar. Si se utiliza una variante de entero, debe estar en el intervalo de 0 a `count`-1, donde `count` es devuelto por la [idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) método.  
  
 `table`  
 [out] Devuelve un [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objeto que representa la tabla deseada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si se especifica una variante de cadena, la cadena de nombres en una tabla determinada. El nombre debe ser uno de los nombres de tabla como se define en [constantes (Debug interfaz Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
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
 [Idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Constantes (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)