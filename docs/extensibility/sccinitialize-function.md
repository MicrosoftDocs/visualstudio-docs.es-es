---
title: "SccInitialize (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccInitialize"
helpviewer_keywords: 
  - "SccInitialize (función)"
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccInitialize (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función inicializa el complemento de control de código fuente y proporciona capacidades y limitaciones para el entorno de desarrollo integrado \(IDE\).  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### Parámetros  
 `ppvContext`  
 \[in\] El complemento de control de código fuente puede colocar un puntero a la estructura de contexto aquí.  
  
 `hWnd`  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 `lpCallerName`  
 \[in\] El nombre del programa de llamada complemento control de código fuente.  
  
 `lpSccName`  
 \[entrada, salida\] El búfer que el complemento de control de código fuente coloca su propio nombre \(no debe exceder de `SCC_NAME_LEN`\).  
  
 `lpSccCaps`  
 \[out\] Devuelve el control de código fuente de marcadores de capacidad del complemento.  
  
 `lpAuxPathLabel`  
 \[entrada, salida\] El búfer que el complemento de control de código fuente coloca una cadena que describe la `lpAuxProjPath` parámetro devuelto por el [SccOpenProject](../extensibility/sccopenproject-function.md) y el [SccGetProjPath](../extensibility/sccgetprojpath-function.md) \(no debe exceder de `SCC_AUXLABEL_LEN`\).  
  
 `pnCheckoutCommentLen`  
 \[out\] Devuelve la longitud máxima permitida para un comentario de desprotección.  
  
 `pnCommentLen`  
 \[out\] Devuelve la longitud máxima permitida para otros comentarios.  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Inicialización del control de origen se realizó correctamente.|  
|SCC\_E\_INITIALIZEFAILED|No se pudo inicializar el sistema.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar la operación especificada.|  
|SCC\_E\_NONSPECFICERROR|Error no específico; no se inicializó el sistema de control de código fuente.|  
  
## Comentarios  
 El IDE llama a esta función cuando se carga el complemento de control de código fuente por primera vez. Permite que el IDE pasar de cierta información, como el nombre del autor de la llamada, el complemento. El IDE también obtiene cierta información como la longitud máxima permitida de comentarios y capacidades del complemento.  
  
 El `ppvContext` apunta a un `NULL` puntero. Puede asignar una estructura para su propio uso y almacenar un puntero a la estructura en el complemento de control de código fuente `ppvContext`. El IDE pasará este puntero para cada función de API VSSCI, lo que permite el complemento para que tenga información de contexto disponible sin recurrir a almacenamiento global y para admitir varias instancias del complemento. Esta estructura debe desasignarse cuando el [SccUninitialize](../extensibility/sccuninitialize-function.md) se llama.  
  
 El `lpCallerName` y `lpSccName` parámetros permiten el IDE y el complemento de control de código fuente para nombres de exchange. Estos nombres pueden utilizarse simplemente para distinguir entre varias instancias, o realmente pueden aparecer en los menús o cuadros de diálogo.  
  
 El `lpAuxPathLabel` parámetro es una cadena que se utiliza como un comentario para identificar la ruta de acceso del proyecto auxiliar que se almacena en el archivo de solución y pasa el control de código fuente del complemento en una llamada a la [SccOpenProject](../extensibility/sccopenproject-function.md).[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] utiliza la cadena "proyecto de SourceSafe:"; otros complementos de control de código fuente deben evitar el uso de esta cadena concreta.  
  
 El `lpSccCaps` parámetro proporciona el control de código fuente complemento un lugar para almacenar los marcadores de bits que indica capacidades del complemento. \(Para obtener una lista completa de los indicadores de capacidad, consulte [Marcadores de capacidad](../extensibility/capability-flags.md)\). Por ejemplo, si los planes para escribir los resultados en una función de devolución de llamada proporcionada por el autor de la llamada, el complemento debe establecer la capacidad de complemento bit SCC\_CAP\_TEXTOUT. Esto podría indicar el IDE para crear una ventana de resultados de control de versión.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Marcadores de capacidad](../extensibility/capability-flags.md)