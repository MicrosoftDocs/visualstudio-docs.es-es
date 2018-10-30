---
title: Idiareadexeatrvacallback | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 69afacf68c77dcb2bca7c951dbd2a1ee9a344cfb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917293"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Lee el número especificado de bytes empezando en el especificado dirección virtual relativa (RVA) del archivo ejecutable.  
  
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