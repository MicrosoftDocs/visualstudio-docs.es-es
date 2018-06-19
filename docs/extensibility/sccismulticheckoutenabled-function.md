---
title: Función SccIsMultiCheckoutEnabled | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: af7102a049cd3db072506cbf492799908196df32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136781"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled (función)
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
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 pbMultiCheckout  
 [out] Especifica si están habilitadas las desprotecciones múltiples para este proyecto (distinto de cero significa que se admiten varias desprotecciones).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La comprobación fue correcta.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 El IDE realiza dos comprobaciones para determinar si los archivos pueden desproteger simultáneamente más de un usuario. En primer lugar, el sistema de control de código fuente debe admitir varias desprotecciones. El complemento de control de código fuente puede especificar esta capacidad durante la inicialización especificando el `SCC_CAP_MULTICHECKOUT`. Por lo tanto, como una segunda comprobación, el IDE llama a esta función para determinar si el proyecto actual no admite varias desprotecciones. Si se admiten varias desprotecciones para el proyecto seleccionado, el complemento devuelve una correcta de código y establece `pbMultiCheckout` a distinto de cero (`TRUE`) o `FALSE`.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)