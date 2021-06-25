---
description: Esta función agrega una lista de archivos del control de código fuente al proyecto abierto actualmente.
title: SccAddFilesFromSCC Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fa08ec93383fa661d1e2dd055b3139b2ba90f34
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904869"
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

[in] Puntero de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] Nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador nulo).

 lpProjPath

[in, out] Cadena auxiliar que identifica el proyecto (hasta `SCC_PRJPATH_` SIZE, incluido el terminador nulo).

 cFiles

[in] Número de archivos especificados por `lpFilePaths` .

 lpFilePaths

[in, out] Matriz de nombres de archivo que se agregarán al proyecto actual.

 lpDestination

[in] Ruta de acceso de destino donde se van a escribir los archivos.

 lpComment

[in] Comentario que se va a aplicar a cada uno de los archivos que se van a agregar.

 pbResults

[in, out] Matriz de marcas que se establecen para indicar un éxito (distinto de cero o TRUE) o un error (cero o FALSE) para cada archivo (el tamaño de la matriz debe ser al menos `cFiles` largo).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|El proyecto no está abierto.|
|SCC_E_OPNOTPERFORMED|La conexión no es al mismo proyecto especificado por `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para actualizar la base de datos.|
|SCC_E_NONSPECIFICERROR|Error desconocido.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
