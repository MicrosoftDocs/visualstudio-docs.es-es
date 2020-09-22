---
title: Función SccPopulateList | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5efdddc448dc8e04ee963eaa1b342a93666d9b62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843075"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función actualiza una lista de archivos para un comando de control de código fuente determinado y proporciona el estado del control de código fuente en todos los archivos especificados.  
  
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
 de Estructura de contexto del complemento de control de código fuente.  
  
 nlínea  
 de Comando de control de código fuente que se aplicará a todos los archivos de la `lpFileNames` matriz (vea el [código de comando](../extensibility/command-code-enumerator.md) para obtener una lista de los comandos posibles).  
  
 N archivos  
 de Número de archivos de la `lpFileNames` matriz.  
  
 lpFileNames  
 de Matriz de nombres de archivo que conoce el IDE.  
  
 pfnPopulate  
 de Función de devolución de llamada IDE a la que se llama para agregar y quitar archivos (vea [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información).  
  
 pvCallerData  
 de Valor que se va a pasar sin cambiar a la función de devolución de llamada.  
  
 lpStatus  
 [in, out] Una matriz para el complemento de control de código fuente para devolver las marcas de estado de cada archivo.  
  
 Opciones  
 de Marcas de comandos (consulte la sección "PopulateList flag" de [marcadores que usan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para obtener más detalles).  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|Correcto.|  
|SCC_E_NONSPECIFICERROR|Error no específico.|  
  
## <a name="remarks"></a>Notas  
 Esta función examina la lista de archivos en busca de su estado actual. Usa la función de devolución de llamada `pfnPopulate` para notificar al llamador cuando un archivo no coincide con los criterios de `nCommand` . Por ejemplo, si el comando es `SCC_COMMAND_CHECKIN` y no se desprotege un archivo de la lista, la devolución de llamada se usa para informar al llamador. En ocasiones, el complemento de control de código fuente puede encontrar otros archivos que pueden formar parte del comando y agregarlos. Esto permite, por ejemplo, que un usuario de Visual Basic desproteja un archivo. bmp utilizado por su proyecto, pero que no aparece en el archivo de proyecto de Visual Basic. Un usuario elige el comando **Get** en el IDE. El IDE mostrará una lista de todos los archivos que cree que el usuario puede obtener, pero antes de que se muestre la lista, `SccPopulateList` se llama a la función para asegurarse de que la lista que se va a mostrar está actualizada.  
  
## <a name="example"></a>Ejemplo  
 El IDE crea una lista de los archivos que considera que el usuario puede obtener. Antes de mostrar esta lista, llama a la `SccPopulateList` función, lo que permite que el complemento de control de código fuente tenga la oportunidad de agregar y eliminar archivos de la lista. El complemento modifica la lista mediante una llamada a la función de devolución de llamada dada (vea [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más detalles).  
  
 El complemento sigue llamando a la `pfnPopulate` función, que agrega y elimina archivos, hasta que termina y, a continuación, vuelve de la `SccPopulateList` función. Después, el IDE puede mostrar la lista. La `lpStatus` matriz representa todos los archivos de la lista original pasados por el IDE. El complemento rellena el estado de todos estos archivos, además de hacer uso de la función de devolución de llamada.  
  
> [!NOTE]
> Un complemento de control de código fuente siempre tiene la opción de devolver inmediatamente desde esta función, lo que sale de la lista. Si un complemento implementa esta función, puede indicarlo estableciendo el `SCC_CAP_POPULATELIST` indicador de bits de capacidad en la primera llamada a [SccInitialize](../extensibility/sccinitialize-function.md). De forma predeterminada, el complemento siempre debe suponer que todos los elementos que se pasan son archivos. Sin embargo, si el IDE establece la `SCC_PL_DIR` marca en el `fOptions` parámetro, todos los elementos que se pasan se consideran directorios. El complemento debe agregar todos los archivos que pertenecen a los directorios. El IDE nunca pasará una mezcla de archivos y directorios.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Marcadores usado por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)
