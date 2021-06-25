---
description: Esta función recupera una variedad de opciones específicas del usuario.
title: SccGetUserOption (Función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 622abc04609edf410214af6b8acf795f969e2fbc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901115"
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

[in] Puntero de contexto del complemento de control de código fuente.

 nOption

[in] Opción para recuperar (vea Comentarios para ver las posibles opciones).

 lpVal

[out] Valor asociado a la opción .

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La opción se recuperó correctamente.|
|SCC_E_OPNOTSUPPORTED|No se admite la opción .|
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|

## <a name="remarks"></a>Observaciones
 Este comando admite las siguientes opciones:

|Opción de usuario|Descripción|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina si el usuario desea comprobar la versión local de los archivos. `lpVal` se asigna `SCC_USEROPT_COLV_YES` (el usuario quiere desasignar los archivos locales) o `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos de error](../extensibility/error-codes.md)
