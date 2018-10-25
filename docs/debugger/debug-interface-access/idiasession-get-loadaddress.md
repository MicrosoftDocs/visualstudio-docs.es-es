---
title: Get_loadaddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2de904777cf09e3289efae71bf585ece9c6444a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864301"
---
# <a name="idiasessiongetloadaddress"></a>IDiaSession::get_loadAddress
Recupera la dirección de carga del archivo ejecutable que se corresponde con los símbolos de este almacén de símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_loadAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve una dirección virtual (VA) donde se ha cargado un archivo .exe o .dll.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La dirección de carga devuelta siempre es cero, a menos que se establezcan específicamente mediante la [Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)