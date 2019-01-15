---
title: 'Idiasourcefile:: | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 750d48cad07251f34e988fa8a6ced618821c443d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825920"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
Recupera el tipo de suma de comprobación.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
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
|0|\<none>|No hay suma de comprobación presente.|  
|1|`CALG_MD5`|la suma de comprobación se genera con el algoritmo hash MD5.|  
|2|`CALG_SHA1`|la suma de comprobación se genera con el algoritmo hash SHA1.|  
  
 El `CryptoAPI` las etiquetas son desde el `ALG_ID` enumeración. Para obtener más información sobre algoritmos hash, consulte el `CryptoAPI` sección de Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Para obtener los bytes de la suma de comprobación real del archivo de origen, llame a la [Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)