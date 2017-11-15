---
title: "CvInitProvider (función) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvInitProvider
helpviewer_keywords: CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ddb249c825048b5bb98dd5b648902663ccd85a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="cvinitprovider-function"></a>CvInitProvider (Función)
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
 [Referencia de la biblioteca de C++](../profiling/cpp-library-reference.md)