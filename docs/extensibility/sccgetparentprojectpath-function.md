---
title: SccGetParentProjectPath (Función) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700712"
---
# <a name="sccgetparentprojectpath-function"></a>Función SccGetParentProjectPath
Esta función determina la ruta de acceso del proyecto primario de un proyecto especificado. Esta función se llama cuando el usuario está agregando un proyecto de Visual Studio al control de código fuente.

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

### <a name="parameters"></a>Parámetros
 pContext

[en] El puntero de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[adentro, fuera] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador NULL).

 lpProjPath

[en] Cadena que identifica la ruta de acceso del proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpAuxProjPath

[adentro, fuera] Cadena auxiliar que identifica el proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpParentProjPath

[adentro, fuera] Cadena de salida que identifica la ruta de acceso del proyecto primario (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La ruta del proyecto principal se obtuvo correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el complemento de control de código fuente.|
|SCC_E_UNKNOWNPROJECT|Project es desconocido para el complemento de control de código fuente.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o inutilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_CONNECTIONFAILURE|Problema de conexión de almacén.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 Esta función devuelve un código de éxito o `lpParentProjPath` error y, si se realiza correctamente, rellena la variable con la ruta de acceso completa del proyecto al proyecto especificado.

 Esta función devuelve la ruta de acceso del proyecto primario de un proyecto existente. Para el proyecto raíz, la función devuelve la ruta de acceso del proyecto que se pasó (es decir, la misma ruta de acceso del proyecto raíz). Tenga en cuenta que una ruta de acceso del proyecto es una cadena que solo es significativa para el complemento de control de código fuente.

 El IDE está preparado para `lpUser` `lpAuxProjPath` aceptar cambios en los parámetros y. El IDE conservará estas cadenas y las pasará a [SccOpenProject](../extensibility/sccopenproject-function.md) cuando el usuario abra este proyecto en el futuro. Estas cadenas, por lo tanto, proporcionan una manera para que el complemento de control de código fuente realice un seguimiento de la información que necesita asociar a un proyecto.

 Esta función es similar a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), excepto que no solicita al usuario que seleccione un proyecto. Tampoco crea un nuevo proyecto, pero solo funciona con un proyecto existente.

 Cuando `SccGetParentProjectPath` se `lpProjPath` llama, y `lpAuxProjPath` no estará vacío y corresponderá a un proyecto válido. Normalmente, el IDE recibe estas cadenas `SccGetProjPath` de una llamada anterior a la función.

 El `lpUser` argumento es el nombre de usuario. El IDE pasará el mismo nombre de usuario `SccGetProjPath` que había recibido previamente de la función y el complemento de control de código fuente debe usar el nombre como valor predeterminado. Si el usuario ya tiene una conexión abierta con el complemento, el complemento debe intentar eliminar cualquier solicitud para asegurarse de que la función funciona en silencio. Sin embargo, si se produce un error en el inicio de sesión, el complemento debe `lpUser`solicitar al usuario un inicio de sesión y, cuando reciba un inicio de sesión válido, vuelva a devolver el nombre en . Dado que el complemento puede cambiar esta cadena, el IDE`SCC_USER_LEN`siempre asignará un búfer de tamaño ( +1). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido (al menos tan válido como la cadena anterior).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas para SccCreateSubProject y SccGetParentProjectPath
 Agregar soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que se solicita a un usuario que seleccione ubicaciones en el sistema de control de código fuente. Visual Studio activa estos cambios si un complemento de control de código fuente admite `SccGetParentProjectPath` las dos funciones nuevas, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) y la función. Sin embargo, la siguiente entrada del Registro se puede usar para deshabilitar estos cambios y revertir al comportamiento anterior de Visual Studio (Source Control Plug-in API Version 1.1):

 **[HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 8.0, SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"-dword:00000001**

 Si esta entrada del Registro no existe o se establece en dword:00000000, Visual Studio intenta usar las nuevas funciones `SccCreateSubProject`y`SccGetParentProjectPath`.

 Si la entrada del Registro se establece en dword:00000001, Visual Studio no intenta usar estas nuevas funciones y las operaciones de agregar al control de código fuente funcionan como lo hacían en versiones anteriores de Visual Studio.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
