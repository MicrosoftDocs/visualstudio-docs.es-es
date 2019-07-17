---
title: IDiaSymbol::findInlineFramesByAddr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4bac80ca02fb64a502bd42fdab1f1e70e453942
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "68149905"
---
# <a name="idiasymbolfindinlineframesbyaddr"></a>IDiaSymbol::findInlineFramesByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos en línea en una dirección determinada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT findInlineFramesByAddr (   
   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `isect`  
 [in] Especifica el componente de la sección de la dirección.  
  
 `offset`  
 [in] Especifica el componente de la dirección de desplazamiento.  
  
 `ppResult`  
 [out] Contiene un `IDiaEnumSymbols` objeto que contiene la lista de fotogramas que se recuperan.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
