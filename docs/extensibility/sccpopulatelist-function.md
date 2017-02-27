---
title: "SccPopulateList (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateList"
helpviewer_keywords: 
  - "SccPopulateList (función)"
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccPopulateList (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función actualiza una lista de archivos para un comando de control de origen determinado y proporciona el estado de control de código fuente en todos los archivos determinados.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 Ncomando  
 \[in\] El comando de control de código fuente que se aplicará a todos los archivos en el `lpFileNames` matriz \(consulte [Código de comando](../extensibility/command-code-enumerator.md) para obtener una lista de comandos posibles\).  
  
 nFiles  
 \[in\] Número de archivos en el `lpFileNames` matriz.  
  
 lpFileNames  
 \[in\] Una matriz de nombres de archivo que se sabe que el IDE.  
  
 pfnPopulate  
 \[in\] La función de devolución de llamada IDE al que llamar para agregar y quitar archivos \(consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más información\).  
  
 pvCallerData  
 \[in\] Valor que se pasa sin cambios a la función de devolución de llamada.  
  
 lpStatus  
 \[entrada, salida\] Una matriz para el control de código fuente para devolver los indicadores de estado para cada archivo.  
  
 Opciones  
 \[in\] Indicadores de comandos \(consulte la sección "PopulateList flag" de [Marcadores de bits que se utilizan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) para obtener más información\).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Correcto.|  
|SCC\_E\_NONSPECIFICERROR|Error no específico.|  
  
## Comentarios  
 Esta función examina la lista de archivos para su estado actual. Usa el `pfnPopulate` la función de devolución de llamada para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`. Por ejemplo, si el comando es `SCC_COMMAND_CHECKIN` y un archivo en la lista no está desprotegido, la devolución de llamada se usa para informar al autor de la llamada. En ocasiones, el complemento de control de código fuente puede encontrar otros archivos que podrían formar parte del comando y agregarlos. Esto permite, por ejemplo, un usuario de Visual Basic desproteger un archivo .bmp que se utiliza en su proyecto pero no aparece en el archivo de proyecto de Visual Basic. Un usuario elige el **obtener** comando en el IDE. El IDE mostrará una lista de todos los archivos que cree que el usuario puede obtener, pero antes de que se muestra la lista, el `SccPopulateList` función se invoca para asegurarse de que la lista para mostrar está actualizada.  
  
## Ejemplo  
 El IDE compila una lista de archivos que cree que puede obtener el usuario. Antes de mostrar esta lista, llama a la `SccPopulateList` de función, que proporciona el complemento de control de origen de la oportunidad de agregar y eliminar archivos de la lista. El complemento modifica la lista mediante una llamada a la función de devolución de llamada determinado \(consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obtener más detalles\).  
  
 El complemento sigue llamando el `pfnPopulate` función, que agrega y elimina los archivos, hasta que finalice y, a continuación, se devuelve desde el `SccPopulateList` \(función\). El IDE puede mostrar su lista. El `lpStatus` matriz representa todos los archivos en la lista original que se pasa en el IDE. Use el complemento rellena el estado de todos estos archivos realizar además de la función de devolución de llamada.  
  
> [!NOTE]
>  Un complemento de control de código fuente siempre tiene la opción de simplemente devolver inmediatamente desde esta función, dejando la lista tal cual. Si un complemento implementa esta función, puede indicar esto estableciendo la `SCC_CAP_POPULATELIST` indicador de capacidad en la primera llamada a la [SccInitialize](../extensibility/sccinitialize-function.md). De forma predeterminada, el complemento siempre debe asumir que todos los elementos que se pasan son archivos. Sin embargo, si establece el IDE la `SCC_PL_DIR` marca en el `fOptions` parámetro, todos los elementos que se pasan deben considerarse directorios. El complemento debe agregar todos los archivos que pertenecen en los directorios. El IDE no pasará nunca en una combinación de archivos y directorios.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Marcadores de bits que se utilizan los comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)   
 [Código de comando](../extensibility/command-code-enumerator.md)