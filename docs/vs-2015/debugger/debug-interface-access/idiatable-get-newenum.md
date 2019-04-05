---
title: IDiaTable::get__NewEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get__NewEnum method
ms.assetid: ee89bba8-5d5c-4a0b-aa0d-1aad56baa380
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3683f646698909150fadb0c9e520f339ce7e50b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996594"
---
# <a name="idiatablegetnewenum"></a>IDiaTable::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el `IUnknown` interfaz que representa el <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
