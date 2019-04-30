---
title: SccGetProjPath (función) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 585402efbda165844f449e2477d5ca69722613a8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446877"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función pide al usuario una ruta de acceso del proyecto, que es una cadena que solo es significativa para el complemento de control de código fuente. Se llama cuando el usuario es:  
  
- Crear un nuevo proyecto  
  
- Agregar un proyecto existente al control de versiones  
  
- Intenta encontrar un proyecto existente de control de versión  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] La estructura de contexto de complemento de control de origen.  
  
 hWnd  
 [in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.  
  
 lpUser  
 [in, out] El nombre de usuario (sin superar SCC_USER_SIZE, incluido el terminador NULL)  
  
 lpProjName  
 [in, out] El nombre del proyecto IDE, área de trabajo del proyecto o archivo MAKE (sin superar SCC_PRJPATH_SIZE, incluido el terminador NULL).  
  
 lpLocalPath  
 [in, out] Ruta de trabajo del proyecto. Si `bAllowChangePath` es `TRUE`, el complemento de control de código fuente puede modificar esta cadena (sin superar _MAX_PATH, incluido el terminador null).  
  
 lpAuxProjPath  
 [in, out] Un búfer para la ruta de acceso de proyecto devuelta (sin superar SCC_PRJPATH_SIZE, incluido el terminador NULL).  
  
 bAllowChangePath  
 [in] Si se trata de `TRUE`, el complemento de control de código fuente puede solicitar y modificar el `lpLocalPath` cadena.  
  
 pbNew  
 [in, out] Estará disponible el valor indica si se debe crear un nuevo proyecto. Valor devuelto indica el éxito de la creación de un proyecto:  
  
|Entrante|Interpretación|  
|--------------|--------------------|  
|true|El usuario puede crear un nuevo proyecto.|  
|false|El usuario no puede crear un nuevo proyecto.|  
  
|Saliente|Interpretación|  
|--------------|--------------------|  
|true|Se crea un nuevo proyecto.|  
|false|Se ha seleccionado un proyecto existente.|  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|El proyecto se creó o se recuperó correctamente.|  
|SCC_I_OPERATIONCANCELED|Se canceló la operación.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención.|  
|SCC_E_CONNECTIONFAILURE|Hubo un problema al intentar conectar con el sistema de control de código fuente.|  
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|  
  
## <a name="remarks"></a>Comentarios  
 El propósito de esta función es para que el IDE adquirir los parámetros `lpProjName` y `lpAuxProjPath`. Después de que el complemento de control de código fuente pide al usuario esta información, transfiere estos dos cadenas a la IDE. El IDE conserva estas cadenas en su archivo de solución y los pasa a la [SccOpenProject](../extensibility/sccopenproject-function.md) cada vez que el usuario abre este proyecto. Estas cadenas de habilitar el complemento realizar un seguimiento de la información asociada a un proyecto.  
  
 Cuando la función se llama en primer lugar, `lpAuxProjPath` se establece en una cadena vacía. `lProjName` También puede estar vacío, o puede contener el nombre de proyecto IDE, que puede usar o ignorar el complemento de control de código fuente. Cuando la función devuelve correctamente, el complemento devuelve las dos cadenas correspondientes. El IDE no hace suposiciones sobre estas cadenas, no los utilizará y no permitirá al usuario modificarlos. Si el usuario desea cambiar la configuración, el IDE llamará `SccGetProjPath` nuevo, pasando los mismos valores ha recibido la última vez. Esto proporciona el complemento control completo sobre estos dos cadenas.  
  
 Para `lpUser`, el IDE puede pasar un nombre de usuario, o simplemente puede pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de origen debe usar de forma predeterminada. Sin embargo, si se ha pasado ningún nombre o error de inicio de sesión con el nombre especificado, el complemento debe solicitar al usuario para un inicio de sesión y pase el nombre nuevo en `lpUser` cuando recibe un inicio de sesión válido. Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
> La primera acción que realiza el IDE puede ser una llamada a la `SccOpenProject` función o el `SccGetProjPath` función. Por lo tanto, ambas tienen un idénticos `lpUser` parámetro, que permite el control de código fuente para iniciar sesión el usuario en cualquier momento. Incluso si el valor devuelto de la función indica un error, el complemento debe rellenar esta cadena con un nombre de inicio de sesión válido.  
  
 `lpLocalPath` es el directorio donde el usuario mantiene el proyecto. Puede ser una cadena vacía. Si no hay ningún directorio definida actualmente (como en el caso de un usuario intenta descargar un proyecto desde el sistema de control de código fuente) y `bAllowChangePath` es `TRUE`, el complemento de control de código fuente puede solicitar al usuario para la entrada o utilizar algún otro método para colocar su cadena en el propietario `lpLocalPath`. Si `bAllowChangePath` es `FALSE`, el complemento no debería cambiar la cadena, porque el usuario ya está trabajando en el directorio especificado.  
  
 Si el usuario crea un nuevo proyecto para que se puede poner bajo control de código fuente, el complemento de control de código fuente podría no realmente crearlo en el sistema de control de código fuente en el momento `SccGetProjPath` se llama. En su lugar, vuelta pasa la cadena junto con un valor distinto de cero para `pbNew`, que indica que el proyecto se creará en el sistema de control de código fuente.  
  
 Por ejemplo, si un usuario de la **nuevo proyecto** asistente en Visual Studio agrega su proyecto al control de código fuente, Visual Studio llama a esta función y el complemento determina si es correcto crear un nuevo proyecto en el sistema de control de origen contiene el proyecto de Visual Studio. Si el usuario hace clic **cancelar** antes de completar el asistente, nunca se crea el proyecto. Si el usuario hace clic **Aceptar**, Visual Studio llama `SccOpenProject`, pasando `SCC_OPT_CREATEIFNEW`, y se crea el proyecto de control de código fuente en ese momento.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
