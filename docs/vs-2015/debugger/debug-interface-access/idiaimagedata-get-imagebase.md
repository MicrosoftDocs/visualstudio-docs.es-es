---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4a8ed3f52a6e4709aa9553b0d7cc906069c9bcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202578"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la ubicación de memoria donde se debe basar la imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 enuncia Devuelve el valor de base de la imagen sugerido.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Debido a conflictos de base de la imagen, una imagen se puede rebasar automáticamente en una ubicación de memoria no utilizada cuando se carga. Este método devuelve la sugerencia base (ubicación de memoria sugerida) que se almacenó en el módulo en tiempo de compilación.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
