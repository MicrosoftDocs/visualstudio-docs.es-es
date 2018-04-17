---
title: Función SccPopulateList | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26e7bbb4a99c3cd649eedb7638feb5b6170b3b59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccpopulatelist-function"></a>SccPopulateList (función)
Esta función actualiza una lista de archivos para un comando de control de origen determinado y proporciona el estado del control de código fuente en todos los archivos determinados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 Ncomando  
 [in] El comando de control de código fuente que se aplicará a todos los archivos en el `lpFileNames` matriz (vea [código comando](../extensibility/command-code-enumerator.md) para obtener una lista de comandos posibles).  
  
 nFiles  
 [in] Número de archivos en el `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Una matriz de nombres de archivo que se sabe que el IDE.  
  
 pfnPopulate  
 [in] La función de devolución de llamada IDE para llamar para agregar y quitar archivos (vea [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información).  
  
 pvCallerData  
 [in] Valor que se pasa sin cambios a la función de devolución de llamada.  
  
 lpStatus  
 [entrada, salida] Una matriz para el complemento para devolver las marcas de estado para cada archivo de control de código fuente.  
  
 fOptions  
 [in] Indicadores de comandos (vea la sección "PopulateList flag" de [marcadores de bits utilizado por determinados comandos](../extensibility/bitflags-used-by-specific-commands.md) para obtener más información).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Correcto.|  
|SCC_E_NONSPECIFICERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función examina la lista de archivos para su estado actual. Usa el `pfnPopulate` función de devolución de llamada para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`. Por ejemplo, si el comando es `SCC_COMMAND_CHECKIN` y no se modifica un archivo en la lista, a continuación, la devolución de llamada se usa para informar al llamador. En ocasiones, el complemento de control de código fuente puede encontrar otros archivos que pudieron formar parte del comando y agregarlos. Esto permite, por ejemplo, un usuario de Visual Basic desproteger un archivo .bmp que se utiliza en su proyecto, pero no aparece en el archivo de proyecto de Visual Basic. Un usuario elige el **obtener** comando en el IDE. El IDE mostrará una lista de todos los archivos que cree que el usuario puede obtener, pero antes de que se muestra la lista, el `SccPopulateList` función se invoca para asegurarse de que la lista para mostrar está actualizada.  
  
## <a name="example"></a>Ejemplo  
 El IDE compila una lista de archivos que cree que puede obtener el usuario. Antes de que muestre esta lista, llama a la `SccPopulateList` de función, lo que proporciona el complemento de control de origen de la oportunidad de agregar y eliminar archivos de la lista. El complemento modifica la lista mediante una llamada a la función de devolución de llamada especificado (vea [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más detalles).  
  
 Continúa el complemento llamar a la `pfnPopulate` función, que agrega y elimina los archivos, hasta que finalice y, a continuación, se devuelve desde el `SccPopulateList` función. El IDE, a continuación, puede mostrar la lista. El `lpStatus` matriz representa todos los archivos de la lista original que se pasa por el IDE. El complemento rellena el estado de todos estos archivos además para hacer que el uso de la función de devolución de llamada.  
  
> [!NOTE]
>  Un complemento de control de origen siempre tiene la opción simplemente devuelvan de inmediato de esta función, dejando la lista tal cual. Si un complemento implementa esta función, puede indicar esto estableciendo el `SCC_CAP_POPULATELIST` indicador de capacidad en la primera llamada a la [SccInitialize](../extensibility/sccinitialize-function.md). De forma predeterminada, el complemento siempre debería suponer que todos los elementos que se pasan son archivos. Sin embargo, si establece el IDE la `SCC_PL_DIR` se marcan en el `fOptions` parámetro, todos los elementos que se pasan tienen que considerarse directorios. El complemento debe agregar todos los archivos que pertenecen en los directorios. El IDE nunca pasará en una combinación de archivos y directorios.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Marcadores de bits utilizada por los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)