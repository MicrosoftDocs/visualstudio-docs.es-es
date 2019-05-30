---
title: SccUninitialize (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71e34352150143c7db207ed31ea6e879f97ca18
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338492"
---
# <a name="sccuninitialize-function"></a>SccUninitialize (Función)
Esta función limpia asignaciones ni las conexiones abiertas que se creó mediante una llamada anterior a la [SccInitialize](../extensibility/sccinitialize-function.md) como preparación para cerrar el complemento de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[in] El puntero a la estructura de contexto de complemento de control de origen que creó en el [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La limpieza que se completó correctamente.|

## <a name="remarks"></a>Comentarios
 El complemento de control de código fuente es responsable de preparación para apagarse y para liberar memoria que ha asignado el complemento para la estructura de contexto. La función se llama una vez para cada instancia determinada de un complemento. Una llamada a la [SccInitialize](../extensibility/sccinitialize-function.md) precede a esta llamada. No hay proyectos todavía pueden estar abiertos en el momento de la llamada a `SccUninitialize`.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)