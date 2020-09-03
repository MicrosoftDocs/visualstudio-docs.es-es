---
title: Función SccEnumChangedFiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ef98c93f02aa8e8a1b4ea53f1998d0ab6713a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200128"
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
 de Puntero de contexto del complemento de control de código fuente.  
  
 hWnd  
 de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.  
  
 cFiles  
 de Número de nombres de archivo especificados en la `lpFileNames` matriz. También especifica el tamaño de la `plIsFileDifferent` matriz.  
  
 lpFileNames  
 de Matriz de nombres de archivo local que se va a comprobar.  
  
 plIsFileDifferent  
 [in, out] Matriz de valores que indican el estado de la diferencia de cada archivo (la matriz debe tener al menos `cFiles` entradas). Distinto de cero significa que el archivo es diferente.  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|Operación completada correctamente.|  
|SCC_UNSPECIFIEDERROR|Error genérico.|  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
