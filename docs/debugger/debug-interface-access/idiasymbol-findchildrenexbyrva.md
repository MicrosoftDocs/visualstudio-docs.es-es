---
title: IDiaSymbol::findChildrenExByRVA | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByRVA
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d1a77ba8527698271356fdc324ccefac2dc0f650
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938869"
---
# <a name="idiasymbolfindchildrenexbyrva"></a>IDiaSymbol::findChildrenExByRVA
Recupera a los elementos secundarios del símbolo que son válidos en una dirección virtual relativa (RVA) especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findChildrenExByRVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `symtag`  
 [in] Especifica las etiquetas de símbolo de los elementos secundarios que se puede recuperar, tal como se define en el [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md). Establecido en `SymTagNull` todos los elementos secundarios van a recuperar.  
  
 `name`  
 [in] Especifica el nombre de los elementos secundarios van a recuperar. Establecido en `NULL` todos los elementos secundarios van a recuperar.  
  
 `compareFlags`  
 [in] Especifica las opciones de comparación que se aplicará a la coincidencia de nombres. Los valores de la [NameSearchOptions (enumeración)](../../debugger/debug-interface-access/namesearchoptions.md) enumeración puede usarse por sí solo o en combinación.  
  
 `address`  
 [in] Especifica la dirección RVA.  
  
 `ppResult`  
 [out] Devuelve un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recupera el objeto que contiene una lista de los símbolos secundarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se ha encontrado al menos un elemento secundario del símbolo, o devuelve `S_FALSE` si no se encuentra ningún elemento secundario; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los símbolos locales que se devuelven incluyen información de rango en vivo.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 Archivo DLL: msdia100.dll  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Enumeración NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)