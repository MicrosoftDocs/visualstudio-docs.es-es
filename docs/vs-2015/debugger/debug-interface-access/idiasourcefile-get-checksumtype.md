---
title: 'Idiasourcefile:: | Microsoft Docs'
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
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 374528b1e48077ba7cd4c1bc25a5cb6d1e87c661
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724815"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el tipo de suma de comprobación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el tipo de suma de comprobación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El tipo de suma de comprobación es un valor que se puede asignar a un algoritmo de suma de comprobación. Por ejemplo, el formato de archivo PDB estándar normalmente puede tener uno de los valores siguientes:  
  
|Tipo de suma de comprobación|Etiqueta de CryptoAPI|Descripción|  
|-------------------|---------------------|-----------------|  
|0|\<Ninguno >|No hay suma de comprobación presente.|  
|1|`CALG_MD5`|la suma de comprobación se genera con el algoritmo hash MD5.|  
|2|`CALG_SHA1`|la suma de comprobación se genera con el algoritmo hash SHA1.|  
  
 El `CryptoAPI` las etiquetas son desde el `ALG_ID` enumeración. Para obtener más información sobre algoritmos hash, consulte el `CryptoAPI` sección de Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)].  
  
 Para obtener los bytes de la suma de comprobación real del archivo de origen, llame a la [Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)



