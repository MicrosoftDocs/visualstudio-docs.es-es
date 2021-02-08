---
title: Función SccRename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4b4579644b04002ae9da3361ba35c63472eef637
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836753"
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

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 lpFileName

de Nombre de archivo completo del archivo cuyo nombre se va a cambiar.

 lpNewName

[in] Nuevo nombre completo. Si la ruta de acceso del directorio es diferente, el archivo se ha despasado de un subdirectorio a otro.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Operación de cambio de nombre completada correctamente.|
|SCC_E_PROJNOTOPEN|El proyecto no está abierto bajo control de código fuente.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención.|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para completar esta operación.|
|SCC_E_COULDNOTCREATEPROJECT|No se pudo crear el proyecto como parte del proceso de cambio de nombre.|
|SCC_E_OPNOTPERFORMED|No se realizó la operación.|
|SCC_E_NONSPECIFICERROR|Se produjo un error no especificado o general.|

## <a name="remarks"></a>Notas
 Esta función se puede usar para cambiar el nombre de un archivo o moverlo de una ubicación a otra en el sistema de control de código fuente. El complemento de control de código fuente no debe intentar tener acceso al archivo en el disco. Es responsabilidad del IDE cambiar el nombre del archivo local.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
