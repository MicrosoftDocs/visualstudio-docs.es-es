---
description: Esta función comprueba si el complemento de control de código fuente permite varias desprotecciones en un archivo.
title: Función SccIsMultiCheckoutEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3ff3943524c37d2150adb0607f62be9b8ddef95
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063804"
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

de Estructura de contexto del complemento de control de código fuente.

 pbMultiCheckout

enuncia Especifica si están habilitadas varias desprotecciones para este proyecto (distinto de cero significa que se admiten varias desprotecciones).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La comprobación se realizó correctamente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 El IDE realiza dos comprobaciones para determinar si más de un usuario puede desproteger los archivos simultáneamente. En primer lugar, el sistema de control de código fuente debe admitir varias desprotecciones. El complemento de control de código fuente puede especificar esta capacidad durante la inicialización especificando `SCC_CAP_MULTICHECKOUT` . Después, como segunda comprobación, el IDE llama a esta función para determinar si el proyecto actual admite o no varias desprotecciones. Si se admiten varias desprotecciones para el proyecto seleccionado, el complemento devuelve un código de éxito y establece `pbMultiCheckout` en un valor distinto de cero ( `TRUE` ) o `FALSE` .

## <a name="see-also"></a>Consulte también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
