---
title: Findsymbolbyaddr | Microsoft Docs
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
- IDiaSession::findSymbolByAddr method
ms.assetid: c130abc5-4d0a-4d2d-8286-94fde36ddd4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edb69dd51e883e23f205d9fb48a2624206d14f41
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746216"
---
# <a name="idiasessionfindsymbolbyaddr"></a>IDiaSession::findSymbolByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un tipo de símbolo especificado que contiene, o más cercana a una dirección especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT findSymbolByAddr (   
   DWORD        isect,  
   DWORD        offset,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `isect`  
 [in] Especifica el componente de la sección de la dirección.  
  
 `offset`  
 [in] Especifica el componente de la dirección de desplazamiento.  
  
 `symtag`  
 [in] Tipo de símbolo que se encuentra. Los valores se toman de la [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) enumeración.  
  
 `ppSymbol`  
 [out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recupera el objeto que representa el símbolo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByAddr( isect, offset, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



