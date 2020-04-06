---
title: Función SccRename (SccRename) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a917e43729b3049e488264c260f8455ab08fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700428"
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

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpFileName

[en] El nombre de archivo completo del archivo que se va a cambiar de nombre.

 lpNewName

[in] Nuevo nombre completo. Si la ruta de acceso del directorio es diferente, el archivo se ha movido de un subdirectorio a otro.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La operación de cambio de nombre se completó correctamente.|
|SCC_E_PROJNOTOPEN|El proyecto no está abierto bajo control de código fuente.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención.|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para completar esta operación.|
|SCC_E_COULDNOTCREATEPROJECT|No se pudo crear el proyecto como parte del proceso de cambio de nombre.|
|SCC_E_OPNOTPERFORMED|La operación no se realizó.|
|SCC_E_NONSPECIFICERROR|Se ha producido un error general o no especificado.|

## <a name="remarks"></a>Observaciones
 Esta función se puede utilizar para cambiar el nombre de un archivo o moverlo de una ubicación a otra en el sistema de control de código fuente. El complemento de control de código fuente no debe intentar acceder al archivo en el disco. Es responsabilidad del IDE cambiar el nombre del archivo local.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
