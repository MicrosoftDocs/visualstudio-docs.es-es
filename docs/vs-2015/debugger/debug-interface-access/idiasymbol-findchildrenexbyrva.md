---
title: IDiaSymbol::findChildrenExByRVA | Documentos de Microsoft
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
- IDiaSymbol::findChildrenExByRVA
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a56a3195d8fd06ac9ae59b0038d3ff395b3d6aa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282716"
---
# <a name="idiasymbolfindchildrenexbyrva"></a>IDiaSymbol::findChildrenExByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera a los elementos secundarios del símbolo que son válidos en una dirección virtual relativa (RVA) especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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



