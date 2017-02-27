---
title: "SccOpenProject (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccOpenProject"
helpviewer_keywords: 
  - "SccOpenProject (función)"
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccOpenProject (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función abre un proyecto de control de código fuente existente o crea uno nuevo.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### Parámetros  
 pvContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 hWnd  
 \[in\] Identificador de la ventana del IDE que se puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 \[entrada, salida\] El nombre del usuario \(no superar SCC\_USER\_SIZE, incluido el terminador NULL\).  
  
 lpProjName  
 \[in\] Cadena que identifica el nombre del proyecto.  
  
 lpLocalProjPath  
 \[in\] La ruta de acceso a la carpeta de trabajo para el proyecto.  
  
 lpAuxProjPath  
 \[entrada, salida\] Una cadena auxiliar opcional que identifica el proyecto \(no superar SCC\_AUXPATH\_SIZE, incluido el terminador NULL\).  
  
 lpComment  
 \[in\] Comentario a un nuevo proyecto que se va a crear.  
  
 lpTextOutProc  
 \[in\] Una función de devolución de llamada opcional para mostrar el texto de salida desde el complemento de control de código fuente.  
  
 dwFlags  
 \[in\] Señales si es necesario crear si el proyecto es desconocido para el origen de un nuevo proyecto de controlan de complemento. Valor puede ser una combinación de `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN.`  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Éxito en la apertura del proyecto.|  
|SCC\_E\_INITIALIZEFAILED|No se pudo inicializar el proyecto.|  
|SCC\_E\_INVALIDUSER|No se pudo iniciar el usuario el sistema de control de código fuente.|  
|SCC\_E\_COULDNOTCREATEPROJECT|El proyecto no existía antes de la llamada;  el `SCC_OPT_CREATEIFNEW` se estableció el indicador, pero no se pudo crear el proyecto.|  
|SCC\_E\_PROJSYNTAXERR|Sintaxis de proyecto no válida.|  
|SCC\_E\_UNKNOWNPROJECT|El proyecto es desconocido para el control de código fuente y el `SCC_OPT_CREATEIFNEW` no se estableció el marcador.|  
|SCC\_E\_INVALIDFILEPATH|Ruta de acceso de archivo no válido o no utilizable.|  
|SCC\_E\_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC\_E\_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de origen, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC\_E\_NONSPECFICERROR|Un error no específico; no se inicializó el sistema de control de código fuente.|  
  
## Comentarios  
 El IDE puede pasar un nombre de usuario \(`lpUser`\), o simplemente puede pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de código fuente debe usar como valor predeterminado. Sin embargo, si se ha pasado ningún nombre o error de inicio de sesión con el nombre especificado, el complemento debe pedir al usuario que inicie sesión y devolverá el nombre válido de `lpUser` cuando recibe un inicio de sesión válido`.` Dado que el complemento puede cambiar la cadena de nombre de usuario, el IDE siempre asignará un búfer de tamaño \(`SCC_USER_LEN`\+ 1 o SCC\_USER\_SIZE, que incluye el espacio para el terminador nulo\).  
  
> [!NOTE]
>  La primera acción que el IDE que deba realizar puede ser una llamada a la `SccOpenProject` función o [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Por este motivo, ambas tienen idéntica `lpUser` parámetro.  
  
 `lpAuxProjPath` y`lpProjName` se leen desde el archivo de solución, o se devuelven de una llamada a la `SccGetProjPath` \(función\). Estos parámetros contienen las cadenas que el complemento de control de código fuente se asocia con el proyecto y sólo son significativos para el complemento. Si ninguna de esas cadenas en el archivo de solución y no se pide al usuario explorar \(que devolvería una cadena a través de la `SccGetProjPath` \(función\)\), el IDE pasa cadenas vacías para `lpAuxProjPath` y `lpProjName`, y se espera que se actualiza el complemento cuando esta función devuelve estos valores.  
  
 `lpTextOutProc` es un puntero a una función de devolución de llamada proporcionada por el IDE para el control de código fuente con el fin de mostrar la salida de resultado del comando. Esta función de devolución de llamada se describe en detalle en [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Si el complemento de control de código fuente tiene intención de sacar partido de esto, debe haber configurado el `SCC_CAP_TEXTOUT` marca en el [SccInitialize](../extensibility/sccinitialize-function.md). Si no se ha establecido esa marca, o si el IDE no admite esta característica, `lpTextOutProc` será `NULL`.  
  
 El `dwFlags` parámetro controla el resultado en caso de que el proyecto está abierto actualmente no existe. Consta de dos marcadores de bits, `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN`. Si el proyecto está abierto ya existe, la función simplemente abre el proyecto y devuelve `SCC_OK`. Si el proyecto no existe y el `SCC_OP_CREATEIFNEW` indicador está activado, puede crear un proyecto en el sistema de control de código fuente, abrirlo y devolver el complemento de control de código fuente `SCC_OK`. Si el proyecto no existe y si el `SCC_OP_CREATEIFNEW` indicador está desactivado, el complemento debe, a continuación, comprobar la `SCC_OP_SILENTOPEN` marca. Si no está en esa marca, el complemento puede pedir al usuario un nombre de proyecto. Si ese marcador está activo, el complemento debe devolver simplemente `SCC_E_UNKNOWNPROJECT`.  
  
## Orden de llamada  
 En el curso normal de eventos, el [SccInitialize](../extensibility/sccinitialize-function.md) se llamaría primero para abrir una sesión de control de código fuente. Una sesión puede constar de una llamada a `SccOpenProject`, seguido por otras llamadas a funciones API de complementos de Control de código fuente y finalizará con una llamada a la [SccCloseProject](../extensibility/scccloseproject-function.md). Esas sesiones pueden repetirse varias veces antes de la [SccUninitialize](../extensibility/sccuninitialize-function.md) se llama.  
  
 Si el origen de conjuntos de complemento de control del `SCC_CAP_REENTRANT` bit en `SccInitialize`, a continuación, la secuencia de la sesión anterior puede repetirse muchas veces en paralelo. Diferentes `pvContext` estructuras de realizar un seguimiento de las distintas sesiones que cada `pvContext` está asociado con un proyecto abierto a la vez. Según la`pvContext` parámetro, el complemento puede determinar qué proyecto se hace referencia en cualquier llamada determinada. Si la capacidad de bits `SCC_CAP_REENTRANT` no está establecida, nonreentrant los complementos de control de código fuente están limitados en su capacidad para trabajar con varios proyectos.  
  
> [!NOTE]
>  El `SCC_CAP_REENTRANT` bits se introdujeron en la versión 1.1 de la API de complementos de Control de código fuente. No se ha establecido o se omite en la versión 1.0 y se supone que todos los versión 1.0 origen control complementos nonreentrant.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)