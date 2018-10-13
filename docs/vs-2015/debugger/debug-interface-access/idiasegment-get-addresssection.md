---
title: Idiasegment | Microsoft Docs
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
- IDiaSegment::get_addressSection method
ms.assetid: 360b61b1-69b1-4a8b-ba37-97a1d835ac53
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4af997096dbb87a651674ca666760caae38b6ac9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177338"
---
# <a name="idiasegmentgetaddresssection"></a>IDiaSegment::get_addressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el número de sección que se asigna a este segmento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el número de sección que se asigna a este segmento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)



