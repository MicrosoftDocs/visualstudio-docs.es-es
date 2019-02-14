---
title: IDiaSession::findFileById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c97df0a5c860fa27fdc136164b9fea79f58fa26
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042145"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Recupera un archivo de código fuente por identificador de archivo de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `uniqueId`  
 [in] Especifica el identificador de archivo de origen.  
  
 `ppResult`  
 [out] Devuelve un [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) recupera el objeto que representa el archivo de origen.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El identificador de archivo de origen es un valor único que se usa internamente para el SDK de DIA para que todos los archivos de origen único. Normalmente, este método se usa internamente para el SDK de DIA.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)