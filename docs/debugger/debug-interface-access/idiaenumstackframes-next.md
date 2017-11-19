---
title: 'Idiaenumstackframes:: Next | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 784744321a76c7142c948bac5c5f83a896d443be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Recupera un número especificado de elementos de marco de pila de la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 [in] El número de elementos de stackframe en el enumerador que se va a recuperar.  
  
 rgelt  
 [out] Una matriz que se rellena con la solicitada [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objetos.  
  
 pceltFetched  
 [out] Devuelve al número de la pila de elementos de marco en el enumerador capturado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún más marcos de pila. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)