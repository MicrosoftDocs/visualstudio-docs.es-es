---
title: Función SccIsMultiCheckoutEnabled ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700582"
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

[en] La estructura de contexto del complemento de control de código fuente.

 pbMultiCheckout

[fuera] Especifica si se habilitan varias desprotecciones para este proyecto (no cero significa que se admiten varias desprotecciones).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El cheque fue exitoso.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 El IDE realiza dos comprobaciones para determinar si más de un usuario puede desproteger los archivos simultáneamente. En primer lugar, el sistema de control de código fuente debe admitir varias desprotecciones. El complemento de control de código fuente puede `SCC_CAP_MULTICHECKOUT`especificar esta capacidad durante la inicialización especificando el archivo . A partir de entonces, como segunda comprobación, el IDE llama a esta función para determinar si el proyecto actual admite o no varias desprotecciones. Si se admiten varias desprotecciones para el proyecto seleccionado, el complemento devuelve un código de éxito y se establece `pbMultiCheckout` en distinto de cero (`TRUE`) o `FALSE`.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
