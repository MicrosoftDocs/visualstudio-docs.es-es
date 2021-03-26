---
description: Esta función recupera una variedad de opciones específicas del usuario.
title: Función SccGetUserOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 262a15069f840c048f574396d5a7ec076760d77e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063960"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption (Función)
Esta función recupera una variedad de opciones específicas del usuario.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parámetros
 pContext

de Puntero de contexto del complemento de control de código fuente.

 nOption

de Opción para recuperar (vea la sección Comentarios para ver las posibles opciones).

 lpVal

enuncia Valor asociado a la opción.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La opción se recuperó correctamente.|
|SCC_E_OPNOTSUPPORTED|No se admite la opción.|
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|

## <a name="remarks"></a>Observaciones
 Este comando admite las siguientes opciones:

|Opción de usuario|Descripción|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina si el usuario desea desproteger la versión local de los archivos. `lpVal` se asigna `SCC_USEROPT_COLV_YES` (el usuario desea desproteger los archivos locales) o `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Consulte también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos de error](../extensibility/error-codes.md)
