---
title: CvIsEnabled (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47129a84b38a4182514bf91be3c55704cf506410
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2018
---
# <a name="cvisenabled-function"></a>CvIsEnabled (Función)
Determina si alguna sesión ha habilitado el proveedor ETW especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```C  
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