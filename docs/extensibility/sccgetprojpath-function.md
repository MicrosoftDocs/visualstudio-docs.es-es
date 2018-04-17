---
title: Función SccGetProjPath | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ef5041b483e85e0806827f7d1188d432b476c5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath (función)
Esta función pide al usuario una ruta de acceso del proyecto, que es una cadena que solo es significativa para el complemento de control de código fuente. Se llama cuando el usuario es:  
  
-   Crear un nuevo proyecto  
  
-   Agregar un proyecto existente al control de versiones  
  
-   Intenta encontrar un proyecto de control de versión existente  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pvContext  
 [in] La estructura de contexto de complemento de control de código fuente.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 [entrada, salida] El nombre de usuario (sin superar SCC_USER_SIZE, incluido el terminador NULL)  
  
 lpProjName  
 [entrada, salida] El nombre del proyecto IDE, área de trabajo del proyecto o archivos MAKE (sin superar SCC_PRJPATH_SIZE, incluido el terminador NULL).  
  
 lpLocalPath  
 [entrada, salida] Ruta de acceso de trabajo del proyecto. Si `bAllowChangePath` es `TRUE`, el complemento de control de código fuente puede modificar esta cadena (sin superar _MAX_PATH, incluido el terminador null).  
  
 lpAuxProjPath  
 [entrada, salida] Un búfer para la ruta de acceso del proyecto devuelta (sin superar SCC_PRJPATH_SIZE, incluido el terminador NULL).  
  
 bAllowChangePath  
 [in] Si se trata de `TRUE`, el complemento de control de código fuente puede solicitar y modificar el `lpLocalPath` cadena.  
  
 pbNew  
 [entrada, salida] Que entran en el valor indica si se debe crear un nuevo proyecto. Valor devuelto indica una ejecución correcta de creación de un proyecto:  
  
|entrante|Interpretación|  
|--------------|--------------------|  
|true|El usuario puede crear un nuevo proyecto.|  
|false|El usuario no puede crear un nuevo proyecto.|  
  
|Saliente|Interpretación|  
|--------------|--------------------|  
|true|Se crea un nuevo proyecto.|  
|false|Se seleccionó un proyecto existente.|  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|El proyecto se creó correctamente o se recuperan.|  
|SCC_I_OPERATIONCANCELED|Se canceló la operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención.|  
|SCC_E_CONNECTIONFAILURE|Hubo un problema al intentar conectar con el sistema de control de código fuente.|  
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|  
  
## <a name="remarks"></a>Comentarios  
 El propósito de esta función es para que el IDE para adquirir los parámetros `lpProjName` y `lpAuxProjPath`. Después de que el complemento de control de código fuente pide al usuario esta información, pasa estos dos cadenas volver al IDE. El IDE conserva estas cadenas en su archivo de solución y los pasa a la [SccOpenProject](../extensibility/sccopenproject-function.md) cada vez que el usuario abre este proyecto. Estas cadenas de habiliten el complemento realizar el seguimiento de información asociada con un proyecto.  
  
 Cuando se llama primero a la función, `lpAuxProjPath` se establece en una cadena vacía. `lProjName` También puede estar vacío, o puede contener el nombre del proyecto IDE, lo que podría usar o ignorar el complemento de control de código fuente. Cuando la función devuelve correctamente, el complemento devuelve las dos cadenas correspondientes. El IDE no hace suposiciones sobre estas cadenas, no los utilizará y no permitirá al usuario modificarlos. Si el usuario desea cambiar la configuración, el IDE llamará `SccGetProjPath` nuevo, pasando los mismos valores había recibido la última vez. Esto proporciona el complemento control completo sobre estas dos cadenas.  
  
 Para `lpUser`, el IDE puede pasar un nombre de usuario o, simplemente puede pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de origen debe usar como valor predeterminado. Sin embargo, si se ha pasado ningún nombre o error de inicio de sesión con el nombre especificado, el complemento debe preguntar al usuario para un inicio de sesión y pase el nombre nuevo en `lpUser` cuando recibe un inicio de sesión válido. Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  La primera acción que realiza el IDE puede ser una llamada a la `SccOpenProject` función o el `SccGetProjPath` (función). Por lo tanto, ambos tienen idéntica `lpUser` parámetro, lo que permite el control de código fuente complemento iniciar sesión del usuario en cualquier momento. Incluso si el valor devuelto de la función indica un error, el complemento debe rellenar esta cadena con un nombre de inicio de sesión válido.  
  
 `lpLocalPath` es el directorio donde el usuario guarda el proyecto. Puede ser una cadena vacía. Si no hay ningún directorio definida actualmente (como en el caso de un usuario intenta descargar un proyecto desde el sistema de control de código fuente) y si `bAllowChangePath` es `TRUE`, el complemento de control de código fuente puede preguntar al usuario para la entrada o utilizar algún otro método para colocar sus cadena en el propietario `lpLocalPath`. Si `bAllowChangePath` es `FALSE`, el complemento no debería cambiar la cadena, porque el usuario ya está trabajando en el directorio especificado.  
  
 Si el usuario crea un nuevo proyecto se deben colocar en el control de código fuente, el complemento de control de código fuente podría no realmente crearlo en el sistema de control de código fuente en el momento `SccGetProjPath` se llama. En su lugar, pase la cadena junto con un valor distinto de cero para `pbNew`, que indica que el proyecto se creará en el sistema de control de código fuente.  
  
 Por ejemplo, si un usuario en el **nuevo proyecto** asistente en Visual Studio agrega su proyecto al control de código fuente, Visual Studio llama a esta función y el complemento determina si es correcto crear un nuevo proyecto en el sistema de control de código fuente para contiene el proyecto de Visual Studio. Si el usuario hace clic en **cancelar** antes de completar el asistente, nunca se crea el proyecto. Si el usuario hace clic en **Aceptar**, Visual Studio llama a `SccOpenProject`, pasando `SCC_OPT_CREATEIFNEW`, y se crea el proyecto de control de código fuente en ese momento.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)