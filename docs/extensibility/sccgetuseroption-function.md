---
title: Función SccGetUserOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd024aa12b263eab7fea4bd80a0e77a3bbad5f1c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721439"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption (Función)
Esta función recupera una variedad de opciones específicas del usuario.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
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

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La opción se recuperó correctamente.|
|SCC_E_OPNOTSUPPORTED|No se admite la opción.|
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|

## <a name="remarks"></a>Comentarios
 Este comando admite las siguientes opciones:

|Opción de usuario|Descripción|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina si el usuario desea desproteger la versión local de los archivos. `lpVal` está asignado `SCC_USEROPT_COLV_YES` (el usuario desea desproteger archivos locales) o `SCC_USEROPT_COLV_NO`.|

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos de error](../extensibility/error-codes.md)