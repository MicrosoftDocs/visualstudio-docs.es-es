---
title: IDiaStackWalker::getEnumFrames2 | Microsoft Docs
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
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf81e33b89a1a4361e73de4d2c532d4da3165f4d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581993"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDiaStackWalker::getEnumFrames2](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalker-getenumframes2).  
  
Recupera un enumerador de marco de pila para un tipo específico de plataforma.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cpuid`  
 [in] Un valor de la [CV_CPU_TYPE_e (enumeración)](../../debugger/debug-interface-access/cv-cpu-type-e.md) enumeración, que especifica el tipo de plataforma.  
  
 `pHelper`  
 [in] La aplicación auxiliar [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) objeto.  
  
 `ppEnum`  
 [out] Devuelve un [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) objeto que contiene una lista de [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objetos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener una lista de marco de pila para simplemente la x86 plataforma, llamada la [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV_CPU_TYPE_e (enumeración)](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)



