---
title: Idiareadexeatoffsetcallback | Microsoft Docs
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
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8202cb3ad7449d282e449fcfd8b284987c8f390d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581835"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Idiareadexeatoffsetcallback](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat).  
  
Lee el número especificado de bytes a partir del desplazamiento especificado desde un archivo ejecutable.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 fileOffset  
 [in] El desplazamiento en el archivo ejecutable al comenzar la lectura.  
  
 cbData  
 [in] Número de bytes que se leen.  
  
 pcbData  
 [out] Devuelve el número de bytes leídos.  
  
 datos]  
 [in, out] Una matriz que se rellena con los bytes leídos del archivo.  
  
## <a name="remarks"></a>Comentarios  
 Este método es invocado por el código de soporte técnico DIA para cargar los bytes de datos de una aplicación ejecutable mediante un desplazamiento de archivo absoluta. Se llama a este método de apoyo del [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)



