---
title: CvIsEnabled (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91a8a0a27456299a914b2919aaf169fa72edf540
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723901"
---
# <a name="cvisenabled-function"></a>CvIsEnabled (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Determina si alguna sesión ha habilitado el proveedor ETW especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `category`  
 Categoría.  
  
 `level`  
 Nivel de importancia.  
  
 `pProvider`  
 Objeto de proveedor válido. No puede ser nulo.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si el proveedor está habilitado actualmente. S_FALSE si el proveedor está deshabilitado actualmente. Código de error en caso de que se hayan producido errores. Utilice la macro FAILED para comprobar si hay alguna condición de error y, a continuación, comprobar S_OK y S_FALSE.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkers.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)



