---
title: SccPopulateList (función) | Documentos de Microsoft
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
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03fedd4854103186eb9d6f034d11a8e0f8b11c9c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279570"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función actualiza una lista de archivos para un comando de control de código fuente concreto y proporciona el estado de control de código fuente en todos los archivos indicados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] La estructura de contexto de complemento de control de origen.  
  
 Ncomando  
 [in] El comando de control de código fuente que se aplicarán a todos los archivos en el `lpFileNames` matriz (consulte [código de comando](../extensibility/command-code-enumerator.md) para obtener una lista de comandos posibles).  
  
 n  
 [in] Número de archivos en el `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Una matriz de nombres de archivo que se sabe que el IDE.  
  
 pfnPopulate  
 [in] La función de devolución de llamada IDE al que llamar para agregar y quitar archivos (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información).  
  
 pvCallerData  
 [in] Valor que se pasa sin cambios a la función de devolución de llamada.  
  
 lpStatus  
 [in, out] Una matriz para el complemento para devolver las marcas de estado para cada archivo de control de código fuente.  
  
 Opciones  
 [in] Indicadores de comandos (consulte la sección "PopulateList marca" de [marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para obtener más información).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Correcto.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función examina la lista de archivos para su estado actual. Usa el `pfnPopulate` función de devolución de llamada para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`. Por ejemplo, si el comando es `SCC_COMMAND_CHECKIN` y no está desprotegido un archivo en la lista y, después, la devolución de llamada se usa para informar al autor de la llamada. En ocasiones, el complemento de control de código fuente puede encontrar otros archivos que podrían formar parte del comando y agregarlos. Esto permite, por ejemplo, un usuario de Visual Basic desproteger un archivo .bmp que utiliza su proyecto pero no aparece en el archivo de proyecto de Visual Basic. Un usuario elige el **obtener** comando en el IDE. El IDE mostrará una lista de todos los archivos que cree que puede obtener el usuario, pero antes de que se muestra la lista, el `SccPopulateList` función se invoca para asegurarse de que está actualizada la lista que se mostrará.  
  
## <a name="example"></a>Ejemplo  
 El IDE compila una lista de archivos que cree que puede obtener el usuario. Antes de mostrar esta lista, llama a la `SccPopulateList` de función, el complemento de control de código fuente se proporciona la oportunidad de agregar y eliminar archivos de la lista. El complemento modifica la lista mediante una llamada a la función de devolución de llamada especificada (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más detalles).  
  
 El complemento sigue llamando al `pfnPopulate` función, que agrega y elimina los archivos, hasta que finalice y, a continuación, se devuelve desde el `SccPopulateList` función. El IDE, a continuación, puede mostrar su lista. El `lpStatus` matriz representa todos los archivos en la lista original pasada por el IDE. El complemento rellena el estado de todos estos archivos además de hacer que el uso de la función de devolución de llamada.  
  
> [!NOTE]
>  Un complemento de control de código fuente siempre tiene la opción de simplemente devuelvan de inmediato de esta función, dejando la lista, ya que es. Si un complemento implementa esta función, puede indicar esto estableciendo la `SCC_CAP_POPULATELIST` indicador de capacidad en la primera llamada a la [SccInitialize](../extensibility/sccinitialize-function.md). De forma predeterminada, el complemento siempre debe asumir que todos los elementos que se pasan son archivos. Sin embargo, si el IDE se establece la `SCC_PL_DIR` marca en el `fOptions` parámetro, todos los elementos que se pasan tienen que considerarse directorios. El complemento debe agregar todos los archivos que pertenecen en los directorios. El IDE nunca pasarán una combinación de archivos y directorios.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Marcadores de bits utilizados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)

