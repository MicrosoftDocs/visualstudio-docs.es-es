---
description: Esta función devuelve funcionalidades adicionales compatibles con el complemento de control de código fuente.
title: Función SccGetExtendedCapabilities | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc047fee2c92f47c181aef455b8175a4e7998176
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905597"
---
# <a name="sccgetextendedcapabilities-function"></a>Función SccGetExtendedCapabilities
Esta función devuelve funcionalidades adicionales compatibles con el complemento de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parámetros
 pContext

[in] Puntero de contexto del complemento de control de código fuente.

 lSccExCaps

[in] Marca que especifica una funcionalidad extendida para la que se va a probar (consulte la tabla Código de funcionalidad extendida en Marcas de funcionalidad [para](../extensibility/capability-flags.md) ver las posibles marcas).

 pbSupported

[out] Devuelve distinto de cero ( `TRUE` ) si se admite la funcionalidad especificada; de lo contrario, devuelve cero ( `FALSE` ).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La operación get capability se completó correctamente.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Error desconocido o no especificado.|

## <a name="remarks"></a>Observaciones
 Este método se llama a petición; Es decir, cuando es necesario probar una funcionalidad, se llama a este método para determinar si se admite esa funcionalidad. Solo se especifica una marca a la vez.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos de error](../extensibility/error-codes.md)
- [Marcas de funcionalidad](../extensibility/capability-flags.md)
