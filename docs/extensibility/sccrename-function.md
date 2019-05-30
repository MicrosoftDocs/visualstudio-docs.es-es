---
title: SccRename (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1329f847f7f961bf4c792cbdf7f40f8f04b1694c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338728"
---
# <a name="sccrename-function"></a>SccRename (Función)
Esta función cambia el nombre de un archivo en el sistema de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[in] La estructura de contexto de complemento de control de origen.

 hWnd

[in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.

 lpFileName

[in] El nombre de archivo completo del archivo que se va a cambiar el nombre.

 lpNewName

[in] El nombre completo de nuevo. Si la ruta de acceso del directorio es diferente, el archivo ha movido de un subdirectorio a otro.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La operación de cambio de nombre que se completó correctamente.|
|SCC_E_PROJNOTOPEN|El proyecto no está abierto en el control de código fuente.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención.|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para completar esta operación.|
|SCC_E_COULDNOTCREATEPROJECT|No se pudo crear el proyecto como parte del proceso de cambio de nombre.|
|SCC_E_OPNOTPERFORMED|No se realizó la operación.|
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado o general.|

## <a name="remarks"></a>Comentarios
 Esta función puede utilizarse para cambiar el nombre de un archivo o moverlo desde una ubicación a otra en el sistema de control de código fuente. El complemento de control de origen no debe intentar tener acceso al archivo en disco. Es responsabilidad del IDE para cambiar el nombre del archivo local.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)