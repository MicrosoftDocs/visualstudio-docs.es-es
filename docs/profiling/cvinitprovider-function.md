---
title: CvInitProvider (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78b7fbb6480f0793b1641159cd3f06c471907603
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750108"
---
# <a name="cvinitprovider-function"></a>Función CvInitProvider
Inicializa el proveedor de marcadores. Se debe llamar antes que cualquier otra función del SDK del visualizador de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```C  
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
 **Encabezado:** *cvmarkers.h*  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca C++](../profiling/cpp-library-reference.md)