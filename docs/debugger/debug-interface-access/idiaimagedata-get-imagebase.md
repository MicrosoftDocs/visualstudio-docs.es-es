---
title: 'Idiaimagedata:: Get_imagebase | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: daaaf26e0a33ce8e90b2b8ac621ed47d299c8276
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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