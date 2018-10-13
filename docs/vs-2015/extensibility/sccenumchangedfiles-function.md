---
title: SccEnumChangedFiles (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4bc5595b5421e0be0139598464e70c6af52df80
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294481"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dada una lista de archivos locales, esta función determina qué archivos son diferentes de las versiones correspondientes en la base de datos de control de código fuente.  
  
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
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 cFiles  
 [in] Número de nombres de archivo especificado en el `lpFileNames` matriz. También especifica el tamaño de `plIsFileDifferent` matriz.  
  
 lpFileNames  
 [in] Matriz de nombres de archivo local para comprobar.  
  
 plIsFileDifferent  
 [in, out] Matriz de valores que indican el estado de la diferencia de cada archivo (matriz debe tener al menos `cFiles` entradas). Distinto de cero significa que el archivo es diferente.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Operación se completó correctamente.|  
|SCC_UNSPECIFIEDERROR|Error genérico.|  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)

