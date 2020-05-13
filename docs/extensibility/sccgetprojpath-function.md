---
title: Función SccGetProjPath ( SccGetProjPath) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700706"
---
# <a name="sccgetprojpath-function"></a>Función SccGetProjPath
Esta función solicita al usuario una ruta de acceso del proyecto, que es una cadena que es significativa solo para el complemento de control de código fuente. Se llama cuando el usuario es:

- Creación de un nuevo proyecto

- Adición de un proyecto existente al control de versiones

- Intentar encontrar un proyecto de control de versiones existente

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

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[adentro, fuera] El nombre de usuario (no debe superar SCC_USER_SIZE, incluido el terminador NULL)

 lpProjName

[adentro, fuera] El nombre del proyecto IDE, el área de trabajo del proyecto o makefile (no debe superar SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpLocalPath

[adentro, fuera] La ruta de trabajo del proyecto. Si `bAllowChangePath` `TRUE`es , el complemento de control de código fuente puede modificar esta cadena (no superar _MAX_PATH, incluido el terminador nulo).

 lpAuxProjPath

[adentro, fuera] Un búfer para la ruta de acceso del proyecto devuelta (no debe superar SCC_PRJPATH_SIZE, incluido el terminador NULL).

 bAllowChangePath

[en] Si se `TRUE`trata , el complemento de control `lpLocalPath` de código fuente puede solicitar y modificar la cadena.

 pbNew

[adentro, fuera] El valor que entra indica si se debe crear un nuevo proyecto. El valor devuelto indica el éxito de la creación de un proyecto:

|Entrante|Interpretación|
|--------------|--------------------|
|TRUE|El usuario puede crear un nuevo proyecto.|
|FALSE|El usuario no puede crear un nuevo proyecto.|

|Saliente|Interpretación|
|--------------|--------------------|
|TRUE|Se creó un nuevo proyecto.|
|FALSE|Se ha seleccionado un proyecto existente.|

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El proyecto se creó o recuperó correctamente.|
|SCC_I_OPERATIONCANCELED|Se canceló la operación.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención.|
|SCC_E_CONNECTIONFAILURE|Se ha producido un problema al intentar conectarse al sistema de control de código fuente.|
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|

## <a name="remarks"></a>Observaciones
 El propósito de esta función es que `lpProjName` `lpAuxProjPath`el IDE adquiera los parámetros y . Después de que el complemento de control de código fuente solicita al usuario esta información, pasa estas dos cadenas de nuevo al IDE. El IDE conserva estas cadenas en su archivo de solución y las pasa a [SccOpenProject](../extensibility/sccopenproject-function.md) cada vez que el usuario abre este proyecto. Estas cadenas permiten al complemento realizar un seguimiento de la información asociada a un proyecto.

 Cuando se llama por `lpAuxProjPath` primera vez a la función, se establece en una cadena vacía. `lProjName`También puede estar vacío o puede contener el nombre del proyecto IDE, que el complemento de control de código fuente puede usar o ignorar. Cuando la función devuelve correctamente, el complemento devuelve las dos cadenas correspondientes. El IDE no hace ninguna suposición sobre estas cadenas, no las usará y no permitirá al usuario modificarlas. Si el usuario desea cambiar la configuración, `SccGetProjPath` el IDE llamará de nuevo, pasando los mismos valores que había recibido la vez anterior. Esto le da al plug-in un control completo sobre estas dos cadenas.

 Para `lpUser`, el IDE puede pasar un nombre de usuario o simplemente puede pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de código fuente debe usarlo como valor predeterminado. Sin embargo, si no se pasó ningún nombre o si el inicio de sesión ha fallado `lpUser` con el nombre especificado, el complemento debe solicitar al usuario un inicio de sesión y devolver el nombre cuando reciba un inicio de sesión válido. Dado que el complemento puede cambiar esta cadena, el IDE`SCC_USER_LEN`siempre asignará un búfer de tamaño ( +1).

> [!NOTE]
> La primera acción que realiza el IDE puede `SccOpenProject` ser `SccGetProjPath` una llamada a la función o a la función. Por lo tanto, ambos `lpUser` tienen un parámetro idéntico, lo que permite que el complemento de control de código fuente inicie sesión en el usuario en cualquier momento. Incluso si la devolución de la función indica un error, el complemento debe rellenar esta cadena con un nombre de inicio de sesión válido.

 `lpLocalPath`es el directorio donde el usuario mantiene el proyecto. Puede ser una cadena vacía. Si no hay ningún directorio definido actualmente (como en el caso de un usuario `bAllowChangePath` `TRUE`que intenta descargar un proyecto desde el sistema de control de código `lpLocalPath`fuente) y si es , el complemento de control de código fuente puede solicitar al usuario la entrada o utilizar algún otro método para colocar su propia cadena en . Si `bAllowChangePath` `FALSE`es , el complemento no debe cambiar la cadena, porque el usuario ya está trabajando en el directorio especificado.

 Si el usuario crea un nuevo proyecto que se pondrá bajo control de código fuente, es `SccGetProjPath` posible que el complemento de control de código fuente no lo cree realmente en el sistema de control de código fuente en el momento. En su lugar, devuelve la cadena junto `pbNew`con un valor distinto de cero para , lo que indica que el proyecto se creará en el sistema de control de código fuente.

 Por ejemplo, si un usuario del Asistente para **nuevo proyecto** en Visual Studio agrega su proyecto al control de código fuente, Visual Studio llama a esta función y el complemento determina si está bien crear un nuevo proyecto en el sistema de control de código fuente que contenga el proyecto de Visual Studio. Si el usuario hace clic en **Cancelar** antes de completar el asistente, el proyecto nunca se crea. Si el usuario **OK**hace clic `SccOpenProject`en Aceptar `SCC_OPT_CREATEIFNEW`, Visual Studio llama a , pasando y el proyecto controlado por código fuente se crea en ese momento.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
