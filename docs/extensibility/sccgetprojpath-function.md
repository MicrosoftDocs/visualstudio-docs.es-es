---
description: Esta función solicita al usuario una ruta de acceso del proyecto, que es una cadena que solo es significativa para el complemento de control de código fuente.
title: Función SccGetProjPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 93266464249b8de037a618bab55ede31988384cb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901076"
---
# <a name="sccgetprojpath-function"></a>Función SccGetProjPath
Esta función solicita al usuario una ruta de acceso del proyecto, que es una cadena que solo es significativa para el complemento de control de código fuente. Se llama cuando el usuario es:

- Creación de un nuevo proyecto

- Agregar un proyecto existente al control de versiones

- Intento de encontrar un proyecto de control de versiones existente

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

### <a name="parameters"></a>Parámetros
 pvContext

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] Nombre de usuario (que no debe superar SCC_USER_SIZE, incluido el terminador NULL)

 lpProjName

[in, out] El nombre del proyecto ide, el área de trabajo del proyecto o el archivo Make (no se debe superar SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpLocalPath

[in, out] Ruta de acceso de trabajo del proyecto. Si es , el complemento de control de código fuente puede modificar esta cadena (no para superar _MAX_PATH, incluido el `bAllowChangePath` `TRUE` terminador null).

 lpProjPath

[in, out] Búfer para la ruta de acceso del proyecto devuelta (no debe superar SCC_PRJPATH_SIZE, incluido el terminador NULL).

 bAllowChangePath

[in] Si es , el complemento de control de código `TRUE` fuente puede solicitar y modificar la `lpLocalPath` cadena.

 pbNew

[in, out] El valor que llega indica si se va a crear un nuevo proyecto. El valor devuelto indica que la creación de un proyecto se ha creado correctamente:

|Entrante|Interpretación|
|--------------|--------------------|
|true|El usuario puede crear un nuevo proyecto.|
|FALSE|Es posible que el usuario no cree un nuevo proyecto.|

|Saliente|Interpretación|
|--------------|--------------------|
|true|Se creó un nuevo proyecto.|
|FALSE|Se ha seleccionado un proyecto existente.|

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El proyecto se creó o recuperó correctamente.|
|SCC_I_OPERATIONCANCELED|Operación cancelada.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención.|
|SCC_E_CONNECTIONFAILURE|Hubo un problema al intentar conectarse al sistema de control de código fuente.|
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|

## <a name="remarks"></a>Observaciones
 El propósito de esta función es que el IDE adquiera los parámetros `lpProjName` y `lpAuxProjPath` . Después de que el complemento de control de código fuente solicite al usuario esta información, vuelve a pasar estas dos cadenas al IDE. El IDE conserva estas cadenas en su archivo de solución y las pasa a [SccOpenProject](../extensibility/sccopenproject-function.md) cada vez que el usuario abre este proyecto. Estas cadenas permiten al complemento realizar un seguimiento de la información asociada a un proyecto.

 Cuando se llama por primera vez a la función, `lpAuxProjPath` se establece en una cadena vacía. `lProjName` también puede estar vacío o puede contener el nombre del proyecto ide, que el complemento de control de código fuente puede usar o omitir. Cuando la función se devuelve correctamente, el complemento devuelve las dos cadenas correspondientes. El IDE no realiza suposiciones sobre estas cadenas, no las usará y no permitirá al usuario modificarlas. Si el usuario desea cambiar la configuración, el IDE llamará de nuevo, pasando los mismos valores `SccGetProjPath` que había recibido la hora anterior. Esto proporciona al complemento control total sobre estas dos cadenas.

 Para , el IDE puede pasar un nombre de usuario o simplemente pasar `lpUser` un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de código fuente debe usarlo como valor predeterminado. Sin embargo, si no se ha pasado ningún nombre o si se ha registrado un error en el inicio de sesión con el nombre especificado, el complemento debe solicitar al usuario un inicio de sesión y devolver el nombre cuando reciba un inicio de sesión `lpUser` válido. Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño ( `SCC_USER_LEN` +1).

> [!NOTE]
> La primera acción que realiza el IDE puede ser una llamada a la `SccOpenProject` función o a la función `SccGetProjPath` . Por lo tanto, ambos tienen un parámetro idéntico, que permite que el complemento de control de código fuente inicie sesión al usuario `lpUser` en cualquier momento. Incluso si la devolución de la función indica un error, el complemento debe rellenar esta cadena con un nombre de inicio de sesión válido.

 `lpLocalPath` es el directorio donde el usuario mantiene el proyecto. Puede ser una cadena vacía. Si no hay ningún directorio definido actualmente (como en el caso de un usuario que intenta descargar un proyecto desde el sistema de control de código fuente) y si es , el complemento de control de código fuente puede solicitar al usuario la entrada o usar algún otro método para colocar su propia cadena `bAllowChangePath` `TRUE` en `lpLocalPath` . Si `bAllowChangePath` es , el complemento no debe cambiar la cadena, porque el usuario ya está `FALSE` trabajando en el directorio especificado.

 Si el usuario crea un proyecto que se va a poner bajo control de código fuente, es posible que el complemento de control de código fuente no lo cree realmente en el sistema de control de código fuente en el momento en que `SccGetProjPath` se llama a . En su lugar, pasa la cadena junto con un valor distinto de cero para , lo que indica que el proyecto se creará `pbNew` en el sistema de control de código fuente.

 Por ejemplo, si un  usuario del Asistente para nuevo proyecto de Visual Studio agrega su proyecto al control de código fuente, Visual Studio llama a esta función y el complemento determina si es correcto crear un nuevo proyecto en el sistema de control de código fuente para que contenga el proyecto Visual Studio. Si el usuario hace clic **en Cancelar** antes de completar el asistente, el proyecto nunca se crea. Si el usuario hace clic en **Aceptar**, Visual Studio llama a , pasando y el proyecto controlado por el origen `SccOpenProject` se crea en ese `SCC_OPT_CREATEIFNEW` momento.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
