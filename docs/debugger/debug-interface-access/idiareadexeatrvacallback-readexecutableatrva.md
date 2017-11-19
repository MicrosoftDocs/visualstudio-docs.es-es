---
title: 'Idiareadexeatrvacallback:: Readexecutableatrva | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 907b75c6021a739ebbe52cbef1ec3e4714360072
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Lee el número especificado de bytes a partir de la especificada dirección virtual relativa (RVA) del archivo ejecutable.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `relativeVirtualAddress`  
 [in] RVA en el archivo ejecutable a comenzar la lectura.  
  
 `cbData`  
 [in] Número de bytes que se va a leer.  
  
 `pcbData`  
 [out] Devuelve el número de bytes leídos.  
  
 `data[]`  
 [entrada, salida] Una matriz que se rellena con los bytes leídos desde el archivo.  
  
## <a name="remarks"></a>Comentarios  
 Este método es invocado por el código de compatibilidad DIA para cargar los bytes de datos de una aplicación ejecutable mediante una dirección virtual relativa. Se llama a este método en apoyo de los [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)