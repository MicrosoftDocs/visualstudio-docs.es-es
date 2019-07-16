---
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f87f5cdd937c0e172e7b96cf0858423b14686d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190738"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera los bytes de la suma de comprobación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
