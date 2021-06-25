---
description: Esta función crea un subproyecto con el nombre especificado en un proyecto primario existente especificado por el argumento lpParentProjPath.
title: Función SccCreateSubProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: a6df7a801d282113b530f24472419a9735256702
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904687"
---
# <a name="scccreatesubproject-function"></a>Función SccCreateSubProject
Esta función crea un subproyecto con el nombre especificado en un proyecto primario existente especificado por el `lpParentProjPath` argumento .

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

[in] Puntero de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] Nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador NULL).

 lpParentProjPath

[in] Cadena que identifica la ruta de acceso del proyecto primario (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpSubProjName

[in] Nombre del subproyecto sugerido (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpProjPath

[in, out] Cadena auxiliar que identifica el proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpSubProjPath

[in, out] Cadena de salida que identifica la ruta de acceso del subproyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El subproyecto se creó correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto primario.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el sistema de control de código fuente.|
|SCC_E_COULDNOTCREATEPROJECT|No se puede crear un subproyecto.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_UNKNOWNPROJECT|El proyecto primario es desconocido para el complemento de control de código fuente.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o inutilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_CONNECTIONFAILURE|Hubo un problema de conexión del complemento de control de código fuente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Si ya existe un subproyecto con el nombre , la función puede cambiar el nombre predeterminado para crear uno único, por ejemplo agregando "_ \<number> " a él. El autor de la llamada debe estar preparado para aceptar cambios `lpUser` en `lpSubProjPath` , y `lpAuxProjPath` . A `lpSubProjPath` `lpAuxProjPath` continuación, los argumentos y se usan en una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md). El autor de la llamada no los debe modificar al devolverse. Estas cadenas proporcionan una manera de que el complemento de control de código fuente realice un seguimiento de la información que necesita asociar a un proyecto. El IDE del autor de la llamada no mostrará estos dos parámetros al devolverse, porque el complemento puede usar una cadena con formato que podría no ser adecuada para su visualización. La función devuelve un código correcto o de error y, si se realiza correctamente, rellena la variable con la ruta de acceso completa del proyecto `lpSubProjPath` al nuevo proyecto.

 Esta función es similar a [SccGetProjPath,](../extensibility/sccgetprojpath-function.md)salvo que crea de forma silenciosa un proyecto en lugar de pedir al usuario que seleccione uno. Cuando se `SccCreateSubProject` llama a la función, y no `lpParentProjName` estará vacía y se `lpAuxProjPath` corresponderá con un proyecto válido. Normalmente, el IDE recibe estas cadenas de una llamada anterior a la función `SccGetProjPath` o [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 El `lpUser` argumento es el nombre de usuario. El IDE pasará el mismo nombre de usuario que había recibido previamente de y el complemento de control de código fuente debe usar el nombre `SccGetProjPath` como valor predeterminado. Si el usuario ya tiene una conexión abierta con el complemento, el complemento debe intentar eliminar las indicaciones para asegurarse de que la función funciona en modo silencioso. Sin embargo, si se produce un error en el inicio de sesión, el complemento debe solicitar al usuario un inicio de sesión y, cuando reciba un inicio de sesión válido, vuelva a pasar el nombre en `lpUser` . Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño (SCC_USER_LEN+1 o SCC_USER_SIZE, que incluye espacio para el terminador nulo). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido (al menos tan válido como la cadena anterior).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas de SccCreateSubProject y SccGetParentProjectPath
 La adición de soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que se solicita al usuario que seleccione ubicaciones en el sistema de control de código fuente. Estos cambios se activan mediante Visual Studio si un complemento de control de código fuente admite las dos funciones nuevas, `SccCreateSubProject` y `SccGetParentProjectPath` . Sin embargo, se puede usar la siguiente entrada del Registro para deshabilitar estos cambios y revertir al comportamiento Visual Studio anterior (API del complemento de control de código fuente versión 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Si esta entrada del Registro no existe o está establecida en dword:000000000, Visual Studio intenta usar las nuevas funciones y `SccCreateSubProject` `SccGetParentProjectPath` .

 Si la entrada del Registro se establece en dword:00000001, Visual Studio no intenta usar estas nuevas funciones y las operaciones de agregar al control de código fuente funcionan como lo hacían en versiones anteriores de Visual Studio.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
