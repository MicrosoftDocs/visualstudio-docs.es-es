---
title: IDiaStackWalkHelper::put_registerValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 417ec6472d815c873972c1ceefaadd6063b3c187
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951578"
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
Establece el valor de un registro.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `index`  
 [in] Un valor de la [CV_HREG_e (enumeración)](../../debugger/debug-interface-access/cv-hreg-e.md) enumeración que especifica el registro para escribir en.  
  
 `NewVal`  
 [in] El nuevo valor del registro.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 A pesar de que el tamaño del valor, una implementación debe almacenar solo de lo que contiene normalmente el registro. Por ejemplo, un registro de 8 bits contendría sólo el 8-bits inferiores del valor especificado.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeración CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)