---
title: Idiaenumstackframes | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b4411d566768b514816fcaaa6386ca91373c159
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581626"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Idiaenumstackframes](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumstackframes-next).  
  
Recupera un número especificado de elementos de marco de pila de la secuencia de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 celt  
 [in] El número de elementos de stackframe del enumerador que se va a recuperar.  
  
 rgelt  
 [out] Una matriz que se rellena con la solicitada [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objetos.  
  
 pceltFetched  
 [out] Devuelve al número de la pila de elementos de marco en el enumerador capturado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún más marcos de pila. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



