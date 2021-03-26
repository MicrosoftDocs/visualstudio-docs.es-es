---
description: Esta función solicita al usuario una ruta de acceso del proyecto, que es una cadena que solo es significativa para el complemento de control de código fuente.
title: Función SccGetProjPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 07c6b8f865d8b1b1d87c9c9468d74e2208265290
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063973"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath función)
Esta función solicita al usuario una ruta de acceso del proyecto, que es una cadena que solo es significativa para el complemento de control de código fuente. Se llama cuando el usuario es:

- Creación de un nuevo proyecto

- Agregar un proyecto existente al control de versiones

- Intentando buscar un proyecto de control de versiones existente

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

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] El nombre de usuario (no debe superar SCC_USER_SIZE, incluido el terminador nulo)

 lpProjName

[in, out] Nombre del proyecto IDE, del área de trabajo del proyecto o del archivo make (sin superar SCC_PRJPATH_SIZE, incluido el terminador nulo).

 lpLocalPath

[in, out] La ruta de trabajo del proyecto. Si `bAllowChangePath` es `TRUE` , el complemento de control de código fuente puede modificar esta cadena (no debe superar _MAX_PATH, incluido el terminador null).

 lpAuxProjPath

[in, out] Búfer de la ruta de acceso del proyecto devuelta (no debe superar SCC_PRJPATH_SIZE, incluido el terminador NULL).

 bAllowChangePath

de Si es `TRUE` , el complemento de control de código fuente puede solicitar y modificar la `lpLocalPath` cadena.

 pbNew

[in, out] Valor que entra en indica si se va a crear un nuevo proyecto. El valor devuelto indica que la creación de un proyecto se ha realizado correctamente:

|Entrante|Interpretación|
|--------------|--------------------|
|TRUE|El usuario puede crear un nuevo proyecto.|
|false|Es posible que el usuario no cree un nuevo proyecto.|

|Saliente|Interpretación|
|--------------|--------------------|
|TRUE|Se creó un nuevo proyecto.|
|false|Se seleccionó un proyecto existente.|

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El proyecto se creó o recuperó correctamente.|
|SCC_I_OPERATIONCANCELED|Operación cancelada.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención.|
|SCC_E_CONNECTIONFAILURE|Hubo un problema al intentar conectarse al sistema de control de código fuente.|
|SCC_E_NONSPECIFICERROR|Se ha producido un error no especificado.|

## <a name="remarks"></a>Observaciones
 El propósito de esta función es que el IDE adquiera los parámetros `lpProjName` y `lpAuxProjPath` . Después de que el complemento de control de código fuente pida esta información al usuario, vuelve a pasar estas dos cadenas al IDE. El IDE conserva estas cadenas en su archivo de solución y las pasa a [SccOpenProject](../extensibility/sccopenproject-function.md) cada vez que el usuario abre este proyecto. Estas cadenas permiten que el complemento realice un seguimiento de la información asociada a un proyecto.

 Cuando se llama a la función por primera vez, `lpAuxProjPath` se establece en una cadena vacía. `lProjName` también puede estar vacío o puede contener el nombre del proyecto IDE, que el complemento de control de código fuente puede utilizar u omitir. Cuando la función devuelve correctamente, el complemento devuelve las dos cadenas correspondientes. El IDE no realiza suposiciones sobre estas cadenas, no las usará y no permitirá al usuario modificarlas. Si el usuario desea cambiar la configuración, el IDE llamará `SccGetProjPath` de nuevo y pasará los mismos valores que había recibido la hora anterior. Esto proporciona al complemento un control completo sobre estas dos cadenas.

 En `lpUser` el caso de, el IDE puede pasar un nombre de usuario o simplemente pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de código fuente debe usarlo como valor predeterminado. Sin embargo, si no se ha pasado ningún nombre o se ha producido un error en el inicio de sesión con el nombre especificado, el complemento debería solicitar al usuario un inicio de sesión y devolver el nombre `lpUser` cuando reciba un inicio de sesión válido. Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño ( `SCC_USER_LEN` + 1).

> [!NOTE]
> La primera acción que realiza el IDE puede ser una llamada a la `SccOpenProject` función o a la `SccGetProjPath` función. Por lo tanto, ambos tienen un `lpUser` parámetro idéntico, que permite que el complemento de control de código fuente inicie la sesión del usuario en cualquier momento. Incluso si la devolución de la función indica un error, el complemento debe rellenar esta cadena con un nombre de inicio de sesión válido.

 `lpLocalPath` es el directorio en el que el usuario mantiene el proyecto. Puede ser una cadena vacía. Si no hay ningún directorio definido actualmente (como en el caso de que un usuario intente descargar un proyecto desde el sistema de control de código fuente) y si `bAllowChangePath` es `TRUE` , el complemento de control de código fuente puede solicitar al usuario una entrada o usar algún otro método para colocar su propia cadena en `lpLocalPath` . Si `bAllowChangePath` es `FALSE` , el complemento no debe cambiar la cadena, porque el usuario ya está trabajando en el directorio especificado.

 Si el usuario crea un nuevo proyecto que se va a colocar bajo control de código fuente, es posible que el complemento de control de código fuente no lo cree realmente en el sistema de control de código fuente en el momento en que `SccGetProjPath` se llama a. En su lugar, devuelve la cadena junto con un valor distinto de cero para `pbNew` , lo que indica que el proyecto se creará en el sistema de control de código fuente.

 Por ejemplo, si un usuario del Asistente para **nuevo proyecto** de Visual Studio agrega su proyecto al control de código fuente, Visual Studio llama a esta función y el complemento determina si es correcto crear un nuevo proyecto en el sistema de control de código fuente para que contenga el proyecto de Visual Studio. Si el usuario hace clic en **Cancelar** antes de completar el asistente, el proyecto nunca se crea. Si el usuario hace clic en **Aceptar**, Visual Studio llama a `SccOpenProject` , pasando `SCC_OPT_CREATEIFNEW` y el proyecto controlado por código fuente se crea en ese momento.

## <a name="see-also"></a>Consulte también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
