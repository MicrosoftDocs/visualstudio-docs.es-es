---
title: Findchildren | Documentos de Microsoft
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
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 684fc0f5474e85806066de352da7ddad8527a3d2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809238"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera a los elementos secundarios del símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `symtag`  
 [in] Especifica las etiquetas de símbolo de los elementos secundarios que se puede recuperar, tal como se define en el [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md). Establecido en `SymTagNull` todos los elementos secundarios van a recuperar.  
  
 `name`  
 [in] Especifica el nombre de los elementos secundarios van a recuperar. Establecido en `NULL` todos los elementos secundarios van a recuperar.  
  
 `compareFlags`  
 [in] Especifica las opciones de comparación que se aplica a la coincidencia de nombres. Los valores de la [NameSearchOptions (enumeración)](../../debugger/debug-interface-access/namesearchoptions.md) enumeración puede usarse por sí solo o en combinación.  
  
 `ppResult`  
 [out] Devuelve un [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recupera el objeto que contiene una lista de los símbolos secundarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se ha encontrado al menos un elemento secundario del símbolo, o devuelve `S_FALSE` si no se encuentra ningún elemento secundario; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método es idéntico a llamar a la [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md) método con este símbolo como primer parámetro.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Enumeración NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)



