---
title: Función SccEnumChangedFiles | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 762bda21f8480224347bd0c8c202c282298e07cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles (función)
Proporciona una lista de archivos locales, esta función determina qué archivos son diferentes de las versiones correspondientes de la base de datos de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 cFiles  
 [in] Número de nombres de archivo especificados en la `lpFileNames` matriz. También especifica el tamaño de `plIsFileDifferent` matriz.  
  
 lpFileNames  
 [in] Matriz de nombres de archivo local para comprobar.  
  
 plIsFileDifferent  
 [entrada, salida] Matriz de valores que indican el estado de la diferencia de cada archivo (matriz debe tener al menos `cFiles` entradas). Es distinto de cero significa que el archivo es diferente.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Operación se completó correctamente.|  
|SCC_UNSPECIFIEDERROR|Error genérico.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)