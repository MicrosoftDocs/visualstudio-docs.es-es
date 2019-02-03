---
title: IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76a5399a0e473172bb94b22cba813512ccf74014
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920570"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Se llama cuando se abre un archivo .pdb de candidato.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdbPath`  
 [in] La ruta de acceso completa del archivo .pdb.  
  
 `resultCode`  
 [in] Código que indica el éxito (`S_OK`) o el fracaso de la carga que se aplican a este archivo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Normalmente, se omite el código de retorno.  
  
## <a name="see-also"></a>Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)