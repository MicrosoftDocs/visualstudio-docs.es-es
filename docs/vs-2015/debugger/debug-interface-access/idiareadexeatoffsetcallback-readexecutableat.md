---
title: Idiareadexeatoffsetcallback | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 113cb31684e55b66c34f775ae6a03cf850977a53
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751242"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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



