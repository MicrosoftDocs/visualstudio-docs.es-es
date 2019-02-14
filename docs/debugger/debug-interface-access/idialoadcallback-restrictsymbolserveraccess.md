---
title: IDiaLoadCallback::RestrictSymbolServerAccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 016f64f4c25b448bbcada095fe5aa41d7c3427a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931302"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Determina si se permite el acceso a un servidor de símbolos para resolver los símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT RestrictSymbolServerAccess();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier código de retorno distinto `S_OK` impide el uso de un servidor de símbolos para resolver los símbolos.  
  
## <a name="see-also"></a>Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)