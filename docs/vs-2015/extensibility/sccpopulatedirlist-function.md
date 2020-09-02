---
title: Función SccPopulateDirList | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6078f0fd90855c432b333fd5967367460d0a364e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200027"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función determina qué directorios y archivos (opcionalmente) se almacenan en el control de código fuente, dada una lista de directorios que se van a examinar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccPopulateDirList(  
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
 de Puntero de contexto del complemento de control de código fuente.  
  
 nDirs  
 de Número de rutas de acceso de directorio en la `lpDirPaths` matriz.  
  
 lpDirPaths  
 de Matriz de rutas de acceso del directorio que se va a examinar.  
  
 pfnPopulate  
 de Función de devolución de llamada a la que se llama para cada ruta de acceso de directorio y (opcionalmente) FILENAME en `lpDirPaths` (vea [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) para obtener más información).  
  
 pvCallerData  
 de Valor que se va a pasar sin cambiar a la función de devolución de llamada.  
  
 Opciones  
 de Combinación de valores que controlan cómo se procesan los directorios (consulte la sección "PopulateDirList flags" de [marcadores que usan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para ver los valores posibles).  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|La operación se completó correctamente.|  
|SCC_E_UNKNOWNERROR|Se produjo un error.|  
  
## <a name="remarks"></a>Observaciones  
 Solo los directorios y los nombres de archivo (opcionalmente) que se encuentran en el repositorio de control de código fuente se pasan a la función de devolución de llamada.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Marcadores usado por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Códigos de error](../extensibility/error-codes.md)
