---
title: 'Idiaenumlinenumbers:: Clone | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumLineNumbers::Clone method
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d58a149a0353a35f3ef9ec1c04b01a2148f8e0dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumlinenumbersclone"></a>IDiaEnumLineNumbers::Clone
Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Clone (   
   IDiaEnumLineNumbers** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppenum`  
 [out] Devuelve un [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objeto que contiene un duplicado del enumerador. La línea de los números no son duplicados, solo el enumerador...  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)