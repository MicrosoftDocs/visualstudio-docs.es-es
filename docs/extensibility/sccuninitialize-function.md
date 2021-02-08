---
title: Función SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e7de3572b17bf47859a64451149a269988c91e5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836688"
---
# <a name="sccuninitialize-function"></a>SccUninitialize (Función)
Esta función limpia las asignaciones o conexiones abiertas creadas por una llamada anterior a [SccInitialize](../extensibility/sccinitialize-function.md) como preparación para cerrar el complemento de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

de Puntero a la estructura de contexto del complemento de control de código fuente creada en [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La limpieza se completó correctamente.|

## <a name="remarks"></a>Notas
 El complemento de control de código fuente es responsable de preparar su cierre y liberar memoria que el complemento ha asignado para la estructura de contexto. Se llama a la función una vez para cada instancia determinada de un complemento. Una llamada a [SccInitialize](../extensibility/sccinitialize-function.md) precede a esta llamada. Todavía no puede haber ningún proyecto abierto en el momento de la llamada a `SccUninitialize` .

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
