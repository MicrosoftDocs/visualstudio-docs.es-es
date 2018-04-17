---
title: 'Idiareadexeatoffsetcallback:: Readexecutableat | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e43bb15eb91e3ffdaa7306140206ca80c2547b0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Lee el número especificado de bytes a partir del desplazamiento especificado desde un archivo ejecutable.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 fileOffset  
 [in] El desplazamiento en el archivo ejecutable a comenzar la lectura.  
  
 cbData  
 [in] Número de bytes que se va a leer.  
  
 pcbData  
 [out] Devuelve el número de bytes leídos.  
  
 datos]  
 [entrada, salida] Una matriz que se rellena de bytes leídos del archivo.  
  
## <a name="remarks"></a>Comentarios  
 Este método es invocado por el código de compatibilidad DIA para cargar los bytes de datos de una aplicación ejecutable mediante un desplazamiento de archivo absoluta. Se llama a este método en apoyo de los [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)