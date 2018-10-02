---
title: Idiareadexeatrvacallback | Microsoft Docs
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
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c0c6f5cfc7c125eb2a90b744ce038c344b192ff
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573824"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Idiareadexeatrvacallback](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva).  
  
Lee el número especificado de bytes empezando en el especificado dirección virtual relativa (RVA) del archivo ejecutable.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `relativeVirtualAddress`  
 [in] La RVA a comenzar la lectura en el archivo ejecutable.  
  
 `cbData`  
 [in] Número de bytes que se leen.  
  
 `pcbData`  
 [out] Devuelve el número de bytes leídos.  
  
 `data[]`  
 [in, out] Una matriz que se rellena con los bytes leídos desde el archivo.  
  
## <a name="remarks"></a>Comentarios  
 Este método es invocado por el código de soporte técnico DIA para cargar los bytes de datos de una aplicación ejecutable mediante una dirección virtual relativa. Se llama a este método de apoyo del [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)



