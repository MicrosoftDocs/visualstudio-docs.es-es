---
title: SccCreateSubProject (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f27226e768d639706e5db777b52a0e4957f70e9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716238"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject (función)
Esta función crea un subproyecto con el nombre especificado en un proyecto existente de elemento primario especificado por el `lpParentProjPath` argumento.

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

[in] El puntero de contexto de complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador NULL).

 lpParentProjPath

[in] Cadena que identifica la ruta de acceso del proyecto principal (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpSubProjName

[in] El nombre sugerido subproyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpAuxProjPath

[in, out] Cadena auxiliar que identifica el proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpSubProjPath

[in, out] Cadena de salida que identifica la ruta de acceso para el subproyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Subproyecto se creó correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto principal.|
|SCC_E_INVALIDUSER|El usuario no ha podido iniciar sesión el sistema de control de origen.|
|SCC_E_COULDNOTCREATEPROJECT|No se puede crear el subproyecto.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válido.|
|SCC_E_UNKNOWNPROJECT|El proyecto principal es desconocido para el complemento de control de código fuente.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válido o no utilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_CONNECTIONFAILURE|Hubo un problema de conexión de complemento de control de origen.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Comentarios
 Si ya existe un subproyecto con el nombre, la función puede cambiar el nombre predeterminado para crear un único, por ejemplo mediante la adición de "_\<número >" a él. El llamador debe estar preparado para aceptar los cambios `lpUser`, `lpSubProjPath`, y `lpAuxProjPath`. El `lpSubProjPath` y`lpAuxProjPath` , a continuación, se usan argumentos en una llamada a la [SccOpenProject](../extensibility/sccopenproject-function.md). No debe modificar el llamador cuando se devuelve. Estas cadenas proporcionan una manera para el control de código fuente para realizar el seguimiento de la información que necesita para asociar a un proyecto de complemento. El llamador IDE no mostrará estos dos parámetros al regresar, porque el complemento puede utilizar una cadena con formato que podría no ser adecuada para su visualización. La función devuelve un código de éxito o error y, si es correcto, rellena la variable `lpSubProjPath` con la ruta de acceso completa del proyecto al nuevo proyecto.

 Esta función es similar a la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), excepto en que crea en modo silencioso un proyecto, en lugar de solicitar al usuario seleccionar uno. Cuando el `SccCreateSubProject` se llama a la función, `lpParentProjName` y `lpAuxProjPath` no estará vacía y se corresponderá con un proyecto válido. Estas cadenas se reciben normalmente por el IDE desde una llamada anterior a la `SccGetProjPath` función o el [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 El `lpUser` argumento es el nombre de usuario. El IDE se pasará en el mismo nombre de usuario que anteriormente recibía de `SccGetProjPath`, y el complemento de control de origen debe usar el nombre de forma predeterminada. Si el usuario ya tiene una conexión abierta con el complemento, a continuación, el complemento debe intentar eliminar las indicaciones para asegurarse de que la función funciona en modo silencioso. Sin embargo, si se produce un error en el inicio de sesión, el complemento debe solicitar al usuario para un inicio de sesión y, cuando recibe un inicio de sesión válido, pase el nombre nuevo en `lpUser`. Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño (SCC_USER_LEN + 1 o SCC_USER_SIZE, que incluye espacio para el terminador nulo). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido (al menos tan válido como la cadena anterior).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas de SccCreateSubProject y SccGetParentProjectPath
 Agregar soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que un usuario se le pide que seleccione las ubicaciones en el sistema de control de código fuente. Estos cambios se activan por Visual Studio si un complemento de control de código fuente admite tanto de las nuevas funciones, `SccCreateSubProject` y `SccGetParentProjectPath`. Sin embargo, puede usarse la siguiente entrada del registro para deshabilitar estos cambios y revertir al comportamiento anterior de Visual Studio (origen de Control de complemento de API versión 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Si esta entrada del registro no existe o está establecida en DWORD: 00000000, Visual Studio intenta usar las nuevas funciones, `SccCreateSubProject` y `SccGetParentProjectPath`.

 Si se establece la entrada del registro a DWORD: 00000001, Visual Studio no intenta usar estas nuevas funciones y las operaciones de agregar a control de código fuente funcionan como lo hacían en versiones anteriores de Visual Studio.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)