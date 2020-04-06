---
title: Función SccAddFilesFromSCC ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701285"
---
# <a name="sccaddfilesfromscc-function"></a>Función SccAddFilesFromSCC
Esta función agrega una lista de archivos del control de código fuente al proyecto abierto actualmente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>Parámetros
 pContext

[en] El puntero de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[adentro, fuera] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador nulo).

 lpAuxProjPath

[adentro, fuera] Cadena auxiliar que identifica el `SCC_PRJPATH_`proyecto (hasta SIZE, incluido el terminador nulo).

 cArchivos

[en] Número de archivos `lpFilePaths`dados por .

 lpFilePaths

[adentro, fuera] Matriz de nombres de archivo para agregar al proyecto actual.

 lpDestination

[en] La ruta de destino donde se van a escribir los archivos.

 lpComment

[en] El comentario que se aplicará a cada uno de los archivos que se van a agregar.

 pbResults

[adentro, fuera] Matriz de indicadores que se establecen para indicar el éxito (no cero o TRUE) o `cFiles` error (cero o FALSE) para cada archivo (el tamaño de la matriz debe ser al menos largo).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|El proyecto no está abierto.|
|SCC_E_OPNOTPERFORMED|La conexión no es al mismo proyecto especificado por`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado a actualizar la base de datos.|
|SCC_E_NONSPECIFICERROR|Error desconocido.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
