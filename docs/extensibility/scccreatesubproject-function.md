---
title: Función SccCreateSubProject ( SccCreateSubProject Function) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701037"
---
# <a name="scccreatesubproject-function"></a>Función SccCreateSubProject
Esta función crea un subproyecto con el nombre especificado `lpParentProjPath` en un proyecto primario existente especificado por el argumento.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>Parámetros
 pContext

[en] El puntero de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[adentro, fuera] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador NULL).

 lpParentProjPath

[en] Cadena que identifica la ruta de acceso del proyecto primario (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpSubProjName

[en] El nombre del subproyecto sugerido (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpAuxProjPath

[adentro, fuera] Cadena auxiliar que identifica el proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpSubProjPath

[adentro, fuera] Cadena de salida que identifica la ruta de acceso del subproyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El subproyecto se creó correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto primario.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el sistema de control de código fuente.|
|SCC_E_COULDNOTCREATEPROJECT|No se puede crear un subproyecto.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_UNKNOWNPROJECT|El proyecto primario es desconocido para el complemento de control de código fuente.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o inutilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_CONNECTIONFAILURE|Se ha producido un problema de conexión de complemento de control de código fuente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 Si ya existe un subproyecto con el nombre, la función puede cambiar el\<nombre predeterminado para crear uno único, por ejemplo, añadiéndole "_ number>". El autor de la llamada `lpUser` `lpSubProjPath`debe `lpAuxProjPath`estar preparado para aceptar cambios en , , y . A `lpSubProjPath` `lpAuxProjPath` continuación, los argumentos y se usan en una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md). No deben ser modificados por el autor de la llamada al regresar. Estas cadenas proporcionan una manera para que el complemento de control de código fuente realice un seguimiento de la información que necesita asociar a un proyecto. El IDE del autor de la llamada no mostrará estos dos parámetros al devolverlos, porque el complemento puede usar una cadena con formato que podría no ser adecuada para su visualización. La función devuelve un código de éxito o `lpSubProjPath` error y, si se realiza correctamente, rellena la variable con la ruta de acceso completa del proyecto al nuevo proyecto.

 Esta función es similar a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), excepto que crea de forma silenciosa un proyecto en lugar de solicitar al usuario que seleccione uno. Cuando `SccCreateSubProject` se llama `lpParentProjName` a `lpAuxProjPath` la función, y no estará vacía y corresponderá a un proyecto válido. Normalmente, el IDE recibe estas cadenas `SccGetProjPath` de una llamada anterior a la función o [sccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 El `lpUser` argumento es el nombre de usuario. El IDE pasará el mismo nombre de usuario `SccGetProjPath`del que había recibido anteriormente , y el complemento de control de código fuente debe usar el nombre como valor predeterminado. Si el usuario ya tiene una conexión abierta con el complemento, el complemento debe intentar eliminar cualquier solicitud para asegurarse de que la función funciona en silencio. Sin embargo, si se produce un error en el inicio de sesión, el complemento debe `lpUser`solicitar al usuario un inicio de sesión y, cuando reciba un inicio de sesión válido, vuelva a devolver el nombre en . Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño (SCC_USER_LEN+1 o SCC_USER_SIZE, que incluye espacio para el terminador nulo). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido (al menos tan válido como la cadena anterior).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas para SccCreateSubProject y SccGetParentProjectPath
 Agregar soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que se solicita a un usuario que seleccione ubicaciones en el sistema de control de código fuente. Visual Studio activa estos cambios si un complemento de control `SccCreateSubProject` de `SccGetParentProjectPath`código fuente admite ambas funciones nuevas y . Sin embargo, la siguiente entrada del Registro se puede usar para deshabilitar estos cambios y revertir al comportamiento anterior de Visual Studio (Source Control Plug-in API Version 1.1):

 **[HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 8.0, SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"-dword:00000001**

 Si esta entrada del Registro no existe o se establece en dword:00000000, Visual Studio intenta usar las nuevas funciones `SccCreateSubProject` y `SccGetParentProjectPath`.

 Si la entrada del Registro se establece en dword:00000001, Visual Studio no intenta usar estas nuevas funciones y las operaciones de agregar al control de código fuente funcionan como lo hacían en versiones anteriores de Visual Studio.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
