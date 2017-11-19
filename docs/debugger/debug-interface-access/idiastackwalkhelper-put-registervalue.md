---
title: IDiaStackWalkHelper::put_registerValue | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abfd209e5c2f59a0c55128eb235fda868f4bfd5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
 [in] Un valor de la [CV_HREG_e (enumeración)](../../debugger/debug-interface-access/cv-hreg-e.md) enumeración que especifica el registro que se va a escribir.  
  
 `NewVal`  
 [in] El nuevo valor del registro.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 A pesar de que el tamaño del valor, una implementación debe almacenar a lo que el registro normalmente contiene únicamente. Por ejemplo, un registro de 8 bits contendría únicamente la 8-bits inferiores del valor especificado.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e (enumeración)](../../debugger/debug-interface-access/cv-hreg-e.md)