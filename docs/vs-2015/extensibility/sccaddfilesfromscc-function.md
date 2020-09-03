---
title: Función SccAddFilesFromSCC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5af748c9180644cae928d1b6db3a3f880b6b286
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200909"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función agrega una lista de archivos del control de código fuente al proyecto actualmente abierto.  
  
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
 de Puntero de contexto del complemento de control de código fuente.  
  
 hWnd  
 de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 [in, out] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador nulo).  
  
 lpAuxProjPath  
 [in, out] Cadena auxiliar que identifica el proyecto (hasta el `SCC_PRJPATH_` tamaño, incluido el terminador nulo).  
  
 cFiles  
 de Número de archivos especificados por `lpFilePaths` .  
  
 lpFilePaths  
 [in, out] Matriz de nombres de archivo que se va a agregar al proyecto actual.  
  
 lpDestination  
 de Ruta de acceso de destino donde se van a escribir los archivos.  
  
 lpComment  
 de Comentario que se va a aplicar a cada uno de los archivos que se van a agregar.  
  
 pbResults  
 [in, out] Matriz de marcas que se establecen para indicar que se ha realizado correctamente (distinto de cero o TRUE) o error (cero o FALSE) para cada archivo (el tamaño de la matriz debe ser al menos `cFiles` largo).  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|El proyecto no está abierto.|  
|SCC_E_OPNOTPERFORMED|La conexión no está en el mismo proyecto que especifica `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|El usuario no está autorizado para actualizar la base de datos.|  
|SCC_E_NONSPECIFICERROR|Error desconocido.|  
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
