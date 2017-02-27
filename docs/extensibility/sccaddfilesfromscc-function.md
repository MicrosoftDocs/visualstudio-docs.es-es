---
title: "SccAddFilesFromSCC (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFilesFromSCC"
helpviewer_keywords: 
  - "SccAddFilesFromSCC (función)"
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAddFilesFromSCC (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función agrega una lista de archivos de control de código fuente al proyecto abierto actualmente.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 pContext  
 \[in\] El puntero de contexto de complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 \[entrada, salida\] El nombre de usuario \(hasta SCC\_USER\_SIZE, incluido el terminador null\).  
  
 lpAuxProjPath  
 \[entrada, salida\] Cadena auxiliar que se identifica el proyecto \(hasta `SCC_PRJPATH_`tamaño, incluido el terminador null\).  
  
 cFiles  
 \[in\] Número de archivos proporcionado por `lpFilePaths`.  
  
 lpFilePaths  
 \[entrada, salida\] Matriz de nombres de archivo para agregar al proyecto actual.  
  
 lpDestination  
 \[in\] La ruta de destino donde están los archivos que se va a escribir.  
  
 lpComment  
 \[in\] El comentario que se aplicará a cada uno de los archivos que se va a agregar.  
  
 pbResults  
 \[entrada, salida\] Matriz de indicadores de conjunto para indicar éxito \(distinto de cero o TRUE\) o no \(cero o FALSE\) para cada archivo \(tamaño de la matriz debe tener al menos `cFiles` largo\).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_E\_PROJNOTOPEN|Proyecto no está abierto.|  
|SCC\_E\_OPNOTPERFORMED|No es el mismo proyecto según lo especificado por conexión `lpAuxProjPath.`|  
|SCC\_E\_NOTAUTHORIZED|Usuario no está autorizado para actualizar la base de datos.|  
|SCC\_E\_NONSPECIFICERROR|Error desconocido.|  
|SCC\_I\_RELOADFILE|Debe volver a cargar un archivo o proyecto.|  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)