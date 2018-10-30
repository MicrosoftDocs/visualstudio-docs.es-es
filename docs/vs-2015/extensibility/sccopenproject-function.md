---
title: SccOpenProject (función) | Microsoft Docs
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
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32f9b085caf0bf49a7be8b6a567b62027653f130
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885569"
---
# <a name="sccopenproject-function"></a>SccOpenProject (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función abre un proyecto de control de código fuente existente o crea uno nuevo.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de origen.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 [in, out] El nombre del usuario (sin superar SCC_USER_SIZE, incluido el terminador NULL).  
  
 lpProjName  
 [in] Cadena que identifica el nombre del proyecto.  
  
 lpLocalProjPath  
 [in] La ruta de acceso a la carpeta de trabajo para el proyecto.  
  
 lpAuxProjPath  
 [in, out] Una cadena auxiliar opcional que identifica el proyecto (sin superar SCC_AUXPATH_SIZE, incluido el terminador NULL).  
  
 lpComment  
 [in] Comentario a un nuevo proyecto que se va a crear.  
  
 lpTextOutProc  
 [in] Una función de devolución de llamada opcional para mostrar el texto de salida desde el complemento de control de código fuente.  
  
 dwFlags  
 [in] Señales si debe crearse si el proyecto es desconocido para el origen de un nuevo proyecto de controlan de complemento. Valor puede ser una combinación de `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN.`  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Éxito al abrir el proyecto.|  
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto.|  
|SCC_E_INVALIDUSER|El usuario no ha podido iniciar sesión el sistema de control de origen.|  
|SCC_E_COULDNOTCREATEPROJECT|El proyecto no existía antes de la llamada;  el `SCC_OPT_CREATEIFNEW` ha establecido la marca, pero no se pudo crear el proyecto.|  
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válido.|  
|SCC_E_UNKNOWNPROJECT|El proyecto es desconocido para el complemento de control de código fuente y el `SCC_OPT_CREATEIFNEW` no ha establecido la marca.|  
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válido o no utilizable.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_NONSPECFICERROR|Un error no específico; no se inicializó el sistema de control de código fuente.|  
  
## <a name="remarks"></a>Comentarios  
 El IDE puede pasar un nombre de usuario (`lpUser`), o simplemente puede pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de origen debe usar de forma predeterminada. Sin embargo, si se ha pasado ningún nombre, o si el error de inicio de sesión con el nombre especificado, el complemento debe pedir al usuario que inicie sesión y devolverá el nombre válido de `lpUser` cuando recibe un inicio de sesión válido`.` porque el complemento puede cambiar la cadena de nombre de usuario , el IDE siempre se asignará un búfer de tamaño (`SCC_USER_LEN`+ 1 o SCC_USER_SIZE, que incluye espacio para el terminador nulo).  
  
> [!NOTE]
>  La primera acción en el IDE es posible que deba realizar puede ser una llamada a la `SccOpenProject` función o el [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Por este motivo, ambos tienen un idénticos `lpUser` parámetro.  
  
 `lpAuxProjPath` y`lpProjName` se leen desde el archivo de solución, o se devuelven en una llamada a la `SccGetProjPath` función. Estos parámetros contienen las cadenas que el complemento de control de código fuente que se asocia con el proyecto y sólo son significativos para el complemento. Si ninguna de esas cadenas están en el archivo de solución y no se solicita al usuario examinar (que devolvería una cadena a través de la `SccGetProjPath` función), el IDE pasa cadenas vacías para ambos `lpAuxProjPath` y `lpProjName`y espera que estos valores para actualizarse por el complemento cuando se devuelve esta función.  
  
 `lpTextOutProc` es un puntero a una función de devolución de llamada proporcionada por el IDE para el complemento con el fin de mostrar la salida de resultado del comando de control de origen. Esta función de devolución de llamada se describe detalladamente en [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Si el complemento de control de código fuente tenga intención de sacar partido de esto, ha establecido la `SCC_CAP_TEXTOUT` marca en el [SccInitialize](../extensibility/sccinitialize-function.md). Si no se ha establecido esa marca, o si el IDE no admite esta característica, `lpTextOutProc` será `NULL`.  
  
 El `dwFlags` parámetro controla el resultado en caso de que el proyecto está abierto actualmente no existe. Consta de dos marcadores de bits, `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN`. Si el proyecto está abierto ya existe, la función simplemente se abre el proyecto y devuelve `SCC_OK`. Si el proyecto no existe y si el `SCC_OP_CREATEIFNEW` indicador está activado, puede crear el proyecto en el sistema de control de código fuente, ábralo y devolver el complemento de control de código fuente `SCC_OK`. Si el proyecto no existe y si el `SCC_OP_CREATEIFNEW` marca está desactivada, el complemento debe, a continuación, busque el `SCC_OP_SILENTOPEN` marca. Si no está en esa marca, el complemento puede solicitar al usuario un nombre de proyecto. Si ese indicador está activado, el complemento debe devolver simplemente `SCC_E_UNKNOWNPROJECT`.  
  
## <a name="calling-order"></a>Orden de llamada  
 En el curso normal de eventos, el [SccInitialize](../extensibility/sccinitialize-function.md) se llamaría primero para abrir una sesión de control de código fuente. Una sesión puede constar de una llamada a `SccOpenProject`, seguido por otras llamadas a funciones API de complemento de Control de código fuente y se terminará con una llamada a la [SccCloseProject](../extensibility/scccloseproject-function.md). Estas sesiones se pueden repetir varias veces antes de la [SccUninitialize](../extensibility/sccuninitialize-function.md) se llama.  
  
 Si el control de origen al complemento establece el `SCC_CAP_REENTRANT` bit en `SccInitialize`, a continuación, la secuencia de la sesión anterior puede repetirse muchas veces en paralelo. Diferentes `pvContext` estructuras realizar un seguimiento de las sesiones diferentes, donde cada `pvContext` está asociado con un proyecto abierto a la vez. Según el`pvContext` parámetro, el complemento puede determinar qué proyecto se hace referencia en cualquier llamada determinada. Si la capacidad de bits `SCC_CAP_REENTRANT` no está establecida, nonreentrant complementos de control de código fuente están limitados en su capacidad para trabajar con varios proyectos.  
  
> [!NOTE]
>  El `SCC_CAP_REENTRANT` bits se introdujeron en la versión 1.1 de la API de complemento de Control de código fuente. No se ha establecido o se omite en la versión 1.0 y se supone que todas las versiones 1.0 complementos código fuente control nonreentrant.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)

