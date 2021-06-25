---
description: Esta función cambia el nombre de un archivo en el sistema de control de código fuente.
title: SccRename (Función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fb3fa392cd4ed31d907fe5913f8d7965a20df05b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900465"
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

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpFileName

[in] Nombre de archivo completo del archivo cuyo nombre se va a cambiar.

 lpNewName

[in] Nuevo nombre completo. Si la ruta de acceso del directorio es diferente, el archivo se ha movido de un subdirectorio a otro.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La operación de cambio de nombre se completó correctamente.|
|SCC_E_PROJNOTOPEN|El proyecto no está abierto bajo control de código fuente.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención.|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para completar esta operación.|
|SCC_E_COULDNOTCREATEPROJECT|No se pudo crear el proyecto como parte del proceso de cambio de nombre.|
|SCC_E_OPNOTPERFORMED|No se realizó la operación.|
|SCC_E_NONSPECIFICERROR|Error general o no especificado.|

## <a name="remarks"></a>Observaciones
 Esta función se puede usar para cambiar el nombre de un archivo o moverlo de una ubicación a otra en el sistema de control de código fuente. El complemento de control de código fuente no debe intentar acceder al archivo en el disco. Es responsabilidad del IDE cambiar el nombre del archivo local.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
