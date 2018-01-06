---
title: "Función SccGetParentProjectPath | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetParentProjectPath
helpviewer_keywords: SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8395d73a48d4c8501ba834b2168b5bcbc8019b8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath (función)
Esta función determina la ruta de acceso del proyecto principal de un proyecto especificado. Esta función se invoca cuando el usuario agrega un proyecto de Visual Studio al control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 [entrada, salida] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador NULL).  
  
 lpProjPath  
 [in] Cadena que identifica la ruta de acceso del proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).  
  
 lpAuxProjPath  
 [entrada, salida] Cadena auxiliar que identifica el proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).  
  
 lpParentProjPath  
 [entrada, salida] Cadena de salida que identifica la ruta de acceso del proyecto principal (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|Ruta de acceso de proyecto principal se obtuvo correctamente.|  
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto.|  
|SCC_E_INVALIDUSER|No se pudo iniciar el usuario el complemento de control de código fuente.|  
|SCC_E_UNKNOWNPROJECT|Proyecto es desconocido para el complemento de control de código fuente.|  
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válido o no utilizable.|  
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|  
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|  
|SCC_E_CONNECTIONFAILURE|Problema de conexión de almacén.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta función devuelve un código de éxito o error y, si es correcto, rellena la variable `lpParentProjPath` con la ruta de acceso completa del proyecto al proyecto especificado.  
  
 Esta función devuelve al elemento primario de ruta de acceso del proyecto de un proyecto existente. Para el proyecto raíz, la función devuelve la ruta de acceso del proyecto que se pasó en (es decir, el mismo proyecto ruta de acceso raíz). Tenga en cuenta que la ruta de acceso de un proyecto es una cadena que solo es significativa para el complemento de control de código fuente.  
  
 El IDE está preparado para aceptar los cambios en el `lpUser` y `lpAuxProjPath` también parámetros. El IDE se conservarán estas cadenas y pasarlos a la [SccOpenProject](../extensibility/sccopenproject-function.md) cuando el usuario abra este proyecto en el futuro. Estas cadenas, por lo tanto, proporcionan una manera para la información de seguimiento que necesita para asociar a un proyecto de complemento de control de código fuente.  
  
 Esta función es similar a la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), salvo que no solicita al usuario que seleccione un proyecto. Nunca se crea un nuevo proyecto pero funciona solo con un proyecto existente.  
  
 Cuando `SccGetParentProjectPath` se llama, `lpProjPath` y `lpAuxProjPath` no estarán vacíos y se corresponderá con un proyecto válido. Estas cadenas se reciben normalmente por el IDE de una llamada anterior a la `SccGetProjPath` (función).  
  
 El `lpUser` argumento es el nombre de usuario. El IDE se pasará en el mismo nombre de usuario que anteriormente recibía desde el `SccGetProjPath` función y el complemento de control de origen deben usar el nombre de forma predeterminada. Si el usuario ya tiene una conexión abierta con el complemento, a continuación, el complemento debe intentar eliminar los mensajes para asegurarse de que la función funciona en modo silencioso. Sin embargo, si se produce un error en el inicio de sesión, el complemento debe preguntar al usuario para un inicio de sesión y, cuando recibe un inicio de sesión válido, pase el nombre nuevo en `lpUser`. Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño (`SCC_USER_LEN`+ 1). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido (al menos tan válido como la cadena anterior).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas de SccCreateSubProject y SccGetParentProjectPath  
 Agregar soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que un usuario debe seleccionar las ubicaciones en el sistema de control de código fuente. Estos cambios se activan mediante Visual Studio si un complemento de control de origen admite tanto de las nuevas funciones, la [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) y `SccGetParentProjectPath` (función). Sin embargo, se puede utilizar la siguiente entrada del registro para deshabilitar estos cambios y revertir al comportamiento anterior de Visual Studio (origen Control complemento API versión 1.1):  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
 Si esta entrada del registro no existe o está establecida en DWORD: 00000000, Visual Studio intenta utilizar las nuevas funciones, `SccCreateSubProject`y`SccGetParentProjectPath`.  
  
 Si la entrada del registro se establece en DWORD: 00000001, Visual Studio no intenta utilizar estas funciones nuevas y las operaciones de agregar al control de código fuente funcionan como lo hacían en versiones anteriores de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)