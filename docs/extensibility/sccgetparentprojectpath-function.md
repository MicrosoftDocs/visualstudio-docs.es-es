---
title: Función SccGetParentProjectPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 825586ed29152bddf0f5dd909f71f96c96db8624
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958406"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath función)
Esta función determina la ruta de acceso del proyecto principal de un proyecto especificado. Se llama a esta función cuando el usuario está agregando un proyecto de Visual Studio al control de código fuente.

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

de Puntero de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] El nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador nulo).

 lpProjPath

de Cadena que identifica la ruta de acceso del proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador nulo).

 lpAuxProjPath

[in, out] Cadena auxiliar que identifica el proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpParentProjPath

[in, out] Cadena de salida que identifica la ruta de acceso del proyecto principal (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La ruta de acceso del proyecto principal se obtuvo correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el complemento de control de código fuente.|
|SCC_E_UNKNOWNPROJECT|El proyecto es desconocido para el complemento de control de código fuente.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o no utilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_CONNECTIONFAILURE|Problema de la conexión del almacén.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Notas
 Esta función devuelve un código de éxito o error y, si se realiza correctamente, rellena la variable `lpParentProjPath` con la ruta de acceso completa del proyecto al proyecto especificado.

 Esta función devuelve la ruta de acceso del proyecto principal de un proyecto existente. En el caso del proyecto raíz, la función devuelve la ruta de acceso del proyecto que se pasó (es decir, la misma ruta de acceso del proyecto raíz). Tenga en cuenta que una ruta de acceso del proyecto es una cadena que solo es significativa para el complemento de control de código fuente.

 El IDE está preparado para aceptar también los cambios en los `lpUser` `lpAuxProjPath` parámetros y. El IDE conservará estas cadenas y las pasará a [SccOpenProject](../extensibility/sccopenproject-function.md) cuando el usuario abra este proyecto en el futuro. Por lo tanto, estas cadenas proporcionan una manera para que el complemento de control de código fuente realice el seguimiento de la información que necesita para asociarse a un proyecto.

 Esta función es similar a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), con la salvedad de que no solicita al usuario que seleccione un proyecto. Tampoco crea nunca un nuevo proyecto, sino que solo funciona con un proyecto existente.

 Cuando `SccGetParentProjectPath` se llama a, `lpProjPath` y `lpAuxProjPath` no estará vacío y se corresponderá con un proyecto válido. Normalmente, el IDE recibe estas cadenas desde una llamada anterior a la `SccGetProjPath` función.

 El `lpUser` argumento es el nombre de usuario. El IDE pasará el mismo nombre de usuario que había recibido anteriormente de la `SccGetProjPath` función, y el complemento de control de código fuente debe utilizar el nombre como valor predeterminado. Si el usuario ya tiene una conexión abierta con el complemento, el complemento debe intentar eliminar los mensajes para asegurarse de que la función funciona de forma silenciosa. Sin embargo, si se produce un error en el inicio de sesión, el complemento debería solicitar al usuario un inicio de sesión y, cuando reciba un inicio de sesión válido, pasar el nombre de nuevo `lpUser` . Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño ( `SCC_USER_LEN` + 1). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido (como mínimo, como la cadena antigua).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas de SccCreateSubProject y SccGetParentProjectPath
 Agregar soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que se solicita al usuario que seleccione ubicaciones en el sistema de control de código fuente. Estos cambios se activan mediante Visual Studio si un complemento de control de código fuente admite las nuevas funciones, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) y la `SccGetParentProjectPath` función. Sin embargo, se puede usar la siguiente entrada del registro para deshabilitar estos cambios y volver al comportamiento anterior de Visual Studio (API de complemento de control de código fuente, versión 1,1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001**

 Si esta entrada del registro no existe o está establecida en DWORD: 00000000, Visual Studio intenta usar las nuevas funciones, `SccCreateSubProject` y `SccGetParentProjectPath` .

 Si la entrada del registro se establece en DWORD: 00000001, Visual Studio no intenta usar estas nuevas funciones y las operaciones de agregar a control de código fuente funcionan como en versiones anteriores de Visual Studio.

## <a name="see-also"></a>Vea también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
