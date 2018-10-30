---
title: Get_imagebase | Microsoft Docs
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
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd514011e81e0881012fa5aa6a19570bd76fb9d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908958"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
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
 [out] Devuelve el valor de base de imagen sugerida.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Debido a conflictos de imagen base, una imagen puede reubicarse automáticamente en una ubicación de memoria no utilizada cuando se cargue. Este método devuelve la sugerencia base (ubicación de memoria recomendados) que se almacenó en el módulo en tiempo de compilación.  
  
## <a name="see-also"></a>Vea también  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)



