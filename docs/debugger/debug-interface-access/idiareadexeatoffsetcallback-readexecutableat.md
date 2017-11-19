---
title: 'Idiareadexeatoffsetcallback:: Readexecutableat | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cb9ff60968d806cfdee0201746a02483895b0af
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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