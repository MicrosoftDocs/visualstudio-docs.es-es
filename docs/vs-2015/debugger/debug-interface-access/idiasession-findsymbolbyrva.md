---
title: IDiaSession::findSymbolByRVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVA method
ms.assetid: 14fb2903-b771-44d6-b0a8-44e0097c58ce
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bc77a6f5e8be35b86f94dc676648f563f7978ee9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144786"
---
# <a name="idiasessionfindsymbolbyrva"></a>IDiaSession::findSymbolByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un tipo de símbolo especificado que contiene o está más cerca de una dirección virtual relativa (RVA) especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT findSymbolByRVA (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rva`  
 de Especifica la RVA.  
  
 `symtag`  
 de Tipo de símbolo que se va a buscar. Los valores se toman de la enumeración de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 enuncia Devuelve un objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el símbolo recuperado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByRVA( rva, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
