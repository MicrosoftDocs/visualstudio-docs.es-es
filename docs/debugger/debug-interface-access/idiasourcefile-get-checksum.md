---
title: Get_checksum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 463720503440771dcbdfbef39703a53cdc875e66
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843351"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Recupera los bytes de la suma de comprobación.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cbData`  
 [in] Tamaño del búfer de datos, en bytes.  
  
 `pcbData`  
 [out] Devuelve el número de bytes de la suma de comprobación. Este parámetro no puede ser `NULL`.  
  
 `data`  
 [in, out] Un búfer que se rellena con los bytes de la suma de comprobación. Si este parámetro es `NULL`, a continuación, `pcbData` devuelve el número de bytes necesarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Para determinar el tipo de algoritmo de suma de comprobación que se usó para generar los bytes de la suma de comprobación, llame a la [Idiasourcefile](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) método.  
  
 La suma de comprobación normalmente se genera a partir de la imagen del archivo de origen para que se reflejen los cambios en el archivo de origen en los cambios en los bytes de la suma de comprobación. Si los bytes de la suma de comprobación no coinciden con una suma de comprobación que se genera a partir de la imagen cargada del archivo, a continuación, se debe considerar el archivo dañado o modificado.  
  
 Las sumas de comprobación típicos nunca son más de 32 bytes de tamaño, pero no suponen que es el tamaño máximo de una suma de comprobación. Establecer el `data` parámetro `NULL` para obtener el número de bytes necesarios para recuperar la suma de comprobación. A continuación, asignar un búfer del tamaño adecuado y llamar a este método una vez más con el nuevo búfer.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)