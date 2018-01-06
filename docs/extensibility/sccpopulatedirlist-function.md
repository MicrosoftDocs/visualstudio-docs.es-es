---
title: "Función SccPopulateDirList | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccPopulateDirList
helpviewer_keywords: SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4be6e63df26d3c4a9b6539276aa97f69e349b83c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList (función)
Esta función determina qué directorios y archivos (opcionalmente) se almacenan en el control de código fuente, dada una lista de directorios que se va a examinar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 nDirs  
 [in] Número de rutas de acceso de directorios en el `lpDirPaths` matriz.  
  
 lpDirPaths  
 [in] Matriz de rutas de acceso de directorios para examinar.  
  
 pfnPopulate  
 [in] Función de devolución de llamada que se llama para cada ruta de acceso de directorio y (opcionalmente) en nombre de archivo en `lpDirPaths` (consulte [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) para obtener más información).  
  
 pvCallerData  
 [in] Valor que se pasa sin cambios a la función de devolución de llamada.  
  
 fOptions  
 [in] Una combinación de valores que controlan cómo se procesan los directorios (vea la sección "PopulateDirList marcas" de [marcadores de bits utilizado por determinados comandos](../extensibility/bitflags-used-by-specific-commands.md) para los valores posibles).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La operación se completó correctamente.|  
|SCC_E_UNKNOWNERROR|Error.|  
  
## <a name="remarks"></a>Comentarios  
 Solo los directorios y (opcionalmente los nombres de archivo que están realmente en el repositorio de control de código fuente) se pasan a la función de devolución de llamada.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Marcadores de bits utilizada por los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Códigos de error](../extensibility/error-codes.md)