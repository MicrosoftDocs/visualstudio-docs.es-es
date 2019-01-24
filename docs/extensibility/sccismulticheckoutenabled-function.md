---
title: SccIsMultiCheckoutEnabled (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ded0e14a1a3d7cbbe1261328672bb6aad89d6628
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874750"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled (Función)
Esta función comprueba si el complemento de control de código fuente permite varias desprotecciones en un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] La estructura de contexto de complemento de control de origen.  
  
 pbMultiCheckout  
 [out] Especifica si las desprotecciones múltiples están habilitadas para este proyecto (distinto de cero significa que se admiten las desprotecciones múltiples).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La comprobación fue correcta.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 El IDE realiza dos comprobaciones para determinar si los archivos pueden desproteger simultáneamente más de un usuario. En primer lugar, el sistema de control de código fuente debe admitir varias desprotecciones. El complemento de control de origen puede especificar esta capacidad durante la inicialización mediante el `SCC_CAP_MULTICHECKOUT`. A partir de entonces, como una segunda comprobación, el IDE llama a esta función para determinar si el proyecto actual no admite varias desprotecciones. Si se admiten varias desprotecciones para el proyecto seleccionado, el complemento devuelve una operación correcta de código y establece `pbMultiCheckout` distinto de cero a (`TRUE`) o `FALSE`.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)