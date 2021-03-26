---
description: Esta función crea un subproyecto con el nombre especificado en un proyecto primario existente especificado por el argumento lpParentProjPath.
title: Función SccCreateSubProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 70568c27afb4bdb5794db64322113dffbd824452
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074007"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject función)
Esta función crea un subproyecto con el nombre especificado en un proyecto primario existente especificado por el `lpParentProjPath` argumento.

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

de Puntero de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador nulo).

 lpParentProjPath

de Cadena que identifica la ruta de acceso del proyecto primario (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpSubProjName

de Nombre sugerido del subproyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador nulo).

 lpAuxProjPath

[in, out] Cadena auxiliar que identifica el proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpSubProjPath

[in, out] Cadena de salida que identifica la ruta de acceso del subproyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El subproyecto se creó correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto primario.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el sistema de control de código fuente.|
|SCC_E_COULDNOTCREATEPROJECT|No se puede crear el subproyecto.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_UNKNOWNPROJECT|El proyecto primario es desconocido para el complemento de control de código fuente.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o no utilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_CONNECTIONFAILURE|Se produjo un problema de conexión del complemento de control de código fuente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Si ya existe un subproyecto con el nombre, la función puede cambiar el nombre predeterminado para crear uno único, por ejemplo, agregando "_ \<number> " a él. El autor de la llamada debe estar preparado para aceptar los cambios en `lpUser` , `lpSubProjPath` y `lpAuxProjPath` . Los `lpSubProjPath` `lpAuxProjPath` argumentos y se utilizan después en una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md). No deben ser modificados por el autor de la llamada después de la devolución. Estas cadenas proporcionan una manera para que el complemento de control de código fuente realice el seguimiento de la información que necesita para asociarse a un proyecto. El IDE del llamador no mostrará estos dos parámetros en la devolución, porque el complemento puede utilizar una cadena con formato que podría no ser adecuada para la visualización. La función devuelve un código de éxito o error y, si se realiza correctamente, rellena la variable `lpSubProjPath` con la ruta de acceso completa del proyecto al nuevo proyecto.

 Esta función es similar a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), con la salvedad de que crea de forma silenciosa un proyecto en lugar de solicitar al usuario que seleccione uno. Cuando `SccCreateSubProject` se llama a la función, `lpParentProjName` y no estará `lpAuxProjPath` vacía y se corresponderá con un proyecto válido. Normalmente, el IDE recibe estas cadenas desde una llamada anterior a la `SccGetProjPath` función o a [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 El `lpUser` argumento es el nombre de usuario. El IDE pasará el mismo nombre de usuario del que había recibido anteriormente `SccGetProjPath` , y el complemento de control de código fuente debe utilizar el nombre como valor predeterminado. Si el usuario ya tiene una conexión abierta con el complemento, el complemento debe intentar eliminar los mensajes para asegurarse de que la función funciona de forma silenciosa. Sin embargo, si se produce un error en el inicio de sesión, el complemento debería solicitar al usuario un inicio de sesión y, cuando reciba un inicio de sesión válido, pasar el nombre de nuevo `lpUser` . Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño (SCC_USER_LEN + 1 o SCC_USER_SIZE, que incluye el espacio para el terminador nulo). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido (como mínimo, como la cadena antigua).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas de SccCreateSubProject y SccGetParentProjectPath
 Agregar soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que se solicita al usuario que seleccione ubicaciones en el sistema de control de código fuente. Estos cambios se activan mediante Visual Studio si un complemento de control de código fuente admite ambas funciones nuevas, `SccCreateSubProject` y `SccGetParentProjectPath` . Sin embargo, se puede usar la siguiente entrada del registro para deshabilitar estos cambios y volver al comportamiento anterior de Visual Studio (API de complemento de control de código fuente, versión 1,1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001**

 Si esta entrada del registro no existe o está establecida en DWORD: 00000000, Visual Studio intenta usar las nuevas funciones, `SccCreateSubProject` y `SccGetParentProjectPath` .

 Si la entrada del registro se establece en DWORD: 00000001, Visual Studio no intenta usar estas nuevas funciones y las operaciones de agregar a control de código fuente funcionan como en versiones anteriores de Visual Studio.

## <a name="see-also"></a>Consulte también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
