---
title: 'Idiatable:: Get__newenum | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get__NewEnum method
ms.assetid: ee89bba8-5d5c-4a0b-aa0d-1aad56baa380
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47a3be463dbf42513480ee2944e246105c686430
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiatablegetnewenum"></a>IDiaTable::get__NewEnum
Recupera el <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el `IUnknown` interfaz que representa la <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)