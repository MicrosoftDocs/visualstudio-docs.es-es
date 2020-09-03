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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190738"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
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
 de Tamaño del búfer de datos, en bytes.  
  
 `pcbData`  
 enuncia Devuelve el número de bytes de suma de comprobación. Este parámetro no puede ser `NULL`.  
  
 `data`  
 [in, out] Búfer que se rellena con los bytes de suma de comprobación. Si este parámetro es `NULL` , `pcbData` devuelve el número de bytes necesarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Para determinar el tipo de algoritmo de suma de comprobación que se usó para generar los bytes de suma de comprobación, llame al método [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .  
  
 La suma de comprobación se genera normalmente a partir de la imagen del archivo de código fuente, por lo que los cambios en el archivo de código fuente se reflejan en los cambios en los bytes de la suma de comprobación. Si los bytes de suma de comprobación no coinciden con una suma de comprobación generada a partir de la imagen cargada del archivo, el archivo se debe considerar dañado o alterado.  
  
 Las sumas de comprobación típicas nunca tienen más de 32 bytes de tamaño, pero no suponen que es el tamaño máximo de una suma de comprobación. Establezca el `data` parámetro en `NULL` para obtener el número de bytes necesarios para recuperar la suma de comprobación. A continuación, asigne un búfer del tamaño adecuado y llame a este método una vez más con el nuevo búfer.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
