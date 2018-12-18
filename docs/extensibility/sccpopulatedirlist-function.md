---
title: SccPopulateDirList (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9b5839735e7564b486444cc0f9b65c71bc06f047
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847999"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList (Función)
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
 [in] Número de rutas de acceso de directorio en el `lpDirPaths` matriz.  
  
 lpDirPaths  
 [in] Matriz de rutas de acceso de directorio para examinar.  
  
 pfnPopulate  
 [in] Función de devolución de llamada para llamar para cada ruta de acceso de directorio y (opcionalmente) en el nombre de archivo `lpDirPaths` (consulte [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) para obtener más información).  
  
 pvCallerData  
 [in] Valor que se pasa sin cambios a la función de devolución de llamada.  
  
 Opciones  
 [in] Una combinación de valores que controlan cómo se procesan los directorios (consulte la sección "PopulateDirList marcas" de [marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) posibles valores).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La operación se completó correctamente.|  
|SCC_E_UNKNOWNERROR|Error.|  
  
## <a name="remarks"></a>Comentarios  
 Solo los directorios y (opcionalmente los nombres de archivo que se encuentran realmente en el repositorio de control de código fuente) se pasan a la función de devolución de llamada.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Códigos de error](../extensibility/error-codes.md)