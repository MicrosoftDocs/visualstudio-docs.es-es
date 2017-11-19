---
title: 'Idiaenumtables:: Next | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d62394ae19d62ad5cdd58b95110442bf33cda8c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Recupera un número especificado de tablas en la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de tablas en el enumerador que se va a recuperar.  
  
 `rgelt`  
 [out] Una matriz que se va a rellenar en con el [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objetos que representan las tablas deseadas.  
  
 `pceltFetched`  
 [out] Devuelve el número de tablas en el enumerador capturado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay más tablas. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)