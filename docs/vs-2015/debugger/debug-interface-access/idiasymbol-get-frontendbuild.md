---
title: Get_frontendbuild | Microsoft Docs
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
- IDiaSymbol::get_frontEndBuild method
ms.assetid: f7dab1c6-112b-4966-baa5-afc976949c76
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 940a7d5b962cd5db2144f0db0059631b702c216c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799411"
---
# <a name="idiasymbolgetfrontendbuild"></a>IDiaSymbol::get_frontEndBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el número de compilación de front-end.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_frontEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Devuelve el número de compilación de front-end. Vea la sección Comentarios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## <a name="remarks"></a>Comentarios  
 Un compilador normalmente se compone de dos elementos principales: el front-end (analizador), que controla el análisis del código fuente en un formato intermedio, y un back-end (generador de código), que convierte el formato intermedio en el ensamblado. No es raro que el front-end tener una versión diferente que el back-end.  
  
 Un front-end o el número de versión de back-end se compone de tres partes: \<principal >.\< secundaria >. \<compilar >, donde \<principales > es el número de versión principal, \<menores > es el número de versión secundaria, y \<compilar > es el número de compilación. Por ejemplo, 13.10.3077.  
  
## <a name="requirements"></a>Requisitos  
  
|Requisito|Descripción|  
|-----------------|-----------------|  
|Encabezado:|Dia2.h|  
|Versión:|SDK de DIA v7.0|  
  
## <a name="see-also"></a>Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



