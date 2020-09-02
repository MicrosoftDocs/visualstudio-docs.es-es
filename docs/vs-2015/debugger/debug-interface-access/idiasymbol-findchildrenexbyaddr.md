---
title: IDiaSymbol::findChildrenExByAddr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f791074d029be78eb7d45e06dce8a8cce145f71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150001"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera los elementos secundarios del símbolo que son válidos en una dirección especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT findChildrenExByAddr (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `symtag`  
 de Especifica las etiquetas de símbolos de los elementos secundarios que se van a recuperar, tal como se define en la [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md). Se establece en `SymTagNull` para todos los elementos secundarios que se van a recuperar.  
  
 `name`  
 de Especifica el nombre de los elementos secundarios que se van a recuperar. Se establece en `NULL` para todos los elementos secundarios que se van a recuperar.  
  
 `compareFlags`  
 de Especifica las opciones de comparación que se aplicarán a la coincidencia de nombres. Los valores de la enumeración [namesearchoptions (](../../debugger/debug-interface-access/namesearchoptions.md) se pueden usar solos o en combinación.  
  
 `address`  
 de Dirección del símbolo.  
  
 `ppResult`  
 enuncia Devuelve un objeto [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contiene una lista de los símbolos secundarios recuperados.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se encontró al menos un elemento secundario del símbolo, o devuelve `S_FALSE` si no se encuentra ningún elemento secundario; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los símbolos locales que se devuelven incluyen información de intervalo en directo.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración Symtagenum (](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession:: Findchildren (](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Enumeración NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
