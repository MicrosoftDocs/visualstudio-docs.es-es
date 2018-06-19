---
title: 'Idiaimagedata:: Get_imagebase | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cd7cb16a4f6a6a629102eafbc212e4b2fff0f00
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458686"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Recupera la ubicación de memoria donde se debe basar la imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el valor de base de imagen sugeridos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Debido a conflictos de base de imagen, una imagen puede reubicarse automáticamente en una ubicación de memoria no utilizada cuando se cargue. Este método devuelve la sugerencia base (ubicación de memoria recomendados) que se almacenó en el módulo en tiempo de compilación.  
  
## <a name="see-also"></a>Vea también  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)