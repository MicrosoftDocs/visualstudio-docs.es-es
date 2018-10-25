---
title: Get_uniqueid | Microsoft Docs
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
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b8262f5ce29478d8de63ad8b5ce4f2740c458f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938286"
---
# <a name="idiasourcefilegetuniqueid"></a>IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un valor de clave de entero simple que es único para esta imagen.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve un valor de clave de entero simple que es único para esta imagen.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Comparar las claves en lugar de cadenas pueden acelerar el proceso de número de línea.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)



