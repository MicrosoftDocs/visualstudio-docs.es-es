---
title: Función SccAddFilesFromSCC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc42a7be878ce52f4d951171c6b5cb08e195d564
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137864"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC (función)
Esta función agrega una lista de archivos de control de código fuente para el proyecto abierto actualmente.  
  
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
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 [entrada, salida] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador null).  
  
 lpAuxProjPath  
 [entrada, salida] Auxiliar cadena que identifica el proyecto (hasta `SCC_PRJPATH_`tamaño, incluido el terminador null).  
  
 cFiles  
 [in] Número de archivos proporcionado por `lpFilePaths`.  
  
 lpFilePaths  
 [entrada, salida] Matriz de nombres de archivo para agregar al proyecto actual.  
  
 lpDestination  
 [in] La ruta de acceso de destino donde están los archivos que se va a escribir.  
  
 lpComment  
 [in] El comentario que se aplicará a cada uno de los archivos que se va a agregar.  
  
 pbResults  
 [entrada, salida] Matriz de marcas de conjunto para indicar una operación correcta (distinto de cero o TRUE) o no (cero o FALSE) para cada archivo (tamaño de la matriz debe tener al menos `cFiles` largo).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Proyecto no está abierto.|  
|SCC_E_OPNOTPERFORMED|Conexión no está en el mismo proyecto según lo especificado por `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Usuario no está autorizado para actualizar la base de datos.|  
|SCC_E_NONSPECIFICERROR|Error desconocido.|  
|SCC_I_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)