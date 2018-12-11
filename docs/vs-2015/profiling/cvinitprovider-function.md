---
title: CvInitProvider (función) | Microsoft Docs
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
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a41e7fe1a6da619e926301b0e1a9b99803fc6d67
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798320"
---
# <a name="cvinitprovider-function"></a>CvInitProvider (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicializa el proveedor de marcadores. Debe llamarse antes que cualquier otra función del SDK del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pGuid`  
 Guid del proveedor. No puede ser nulo.  
  
 `ppProvider`  
 Dirección de una variable de salida que almacenará el contexto del proveedor. No puede ser nulo.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK cuando el proveedor se inicializa correctamente, o código de error en caso de que se hayan producido errores. Utilice macros SUCCEEDED/FAILED para comprobar si existe una condición de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cvmarkers.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)



