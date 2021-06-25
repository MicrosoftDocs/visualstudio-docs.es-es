---
description: Esta función determina la ruta de acceso del proyecto primario de un proyecto especificado.
title: Función SccGetParentProjectPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a0a77808004c7bc8f408bbf34a3ed4f0715b36
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900140"
---
# <a name="sccgetparentprojectpath-function"></a>Función SccGetParentProjectPath
Esta función determina la ruta de acceso del proyecto primario de un proyecto especificado. Se llama a esta función cuando el usuario agrega un proyecto Visual Studio al control de código fuente.

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

[in] Puntero de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] Nombre de usuario (hasta SCC_USER_SIZE, incluido el terminador NULL).

 lpProjPath

[in] Cadena que identifica la ruta de acceso del proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpProjPath

[in, out] Cadena auxiliar que identifica el proyecto (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

 lpParentProjPath

[in, out] Cadena de salida que identifica la ruta de acceso del proyecto principal (hasta SCC_PRJPATH_SIZE, incluido el terminador NULL).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La ruta de acceso del proyecto primario se obtuvo correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el complemento de control de código fuente.|
|SCC_E_UNKNOWNPROJECT|El proyecto es desconocido para el complemento de control de código fuente.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o inutilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_CONNECTIONFAILURE|Problema de conexión de almacenamiento.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Esta función devuelve un código correcto o de error y, si se realiza correctamente, rellena la variable con la ruta de acceso completa del proyecto `lpParentProjPath` al proyecto especificado.

 Esta función devuelve la ruta de acceso del proyecto primario de un proyecto existente. Para el proyecto raíz, la función devuelve la ruta de acceso del proyecto que se pasó (es decir, la misma ruta de acceso del proyecto raíz). Tenga en cuenta que una ruta de acceso del proyecto es una cadena que solo es significativa para el complemento de control de código fuente.

 El IDE también está preparado para aceptar cambios en los `lpUser` `lpAuxProjPath` parámetros y . El IDE conservará estas cadenas y las pasará a [SccOpenProject](../extensibility/sccopenproject-function.md) cuando el usuario abra este proyecto en el futuro. Por lo tanto, estas cadenas proporcionan una manera de que el complemento de control de código fuente realice el seguimiento de la información que necesita asociar a un proyecto.

 Esta función es similar a [SccGetProjPath](../extensibility/sccgetprojpath-function.md), salvo que no solicita al usuario que seleccione un proyecto. Tampoco crea nunca un proyecto nuevo, pero solo funciona con un proyecto existente.

 Cuando `SccGetParentProjectPath` se llama a , y no estará vacío y se `lpProjPath` `lpAuxProjPath` corresponderá con un proyecto válido. El IDE suele recibir estas cadenas de una llamada anterior a la `SccGetProjPath` función.

 El `lpUser` argumento es el nombre de usuario. El IDE pasará el mismo nombre de usuario que había recibido previamente de la función y el complemento de control de código fuente debe usar el nombre `SccGetProjPath` como valor predeterminado. Si el usuario ya tiene una conexión abierta con el complemento, el complemento debe intentar eliminar las indicaciones para asegurarse de que la función funciona en modo silencioso. Sin embargo, si se produce un error en el inicio de sesión, el complemento debe solicitar al usuario un inicio de sesión y, cuando reciba un inicio de sesión válido, vuelva a pasar el nombre en `lpUser` . Dado que el complemento puede cambiar esta cadena, el IDE siempre asignará un búfer de tamaño ( `SCC_USER_LEN` +1). Si se cambia la cadena, la nueva cadena debe ser un nombre de inicio de sesión válido (al menos tan válido como la cadena anterior).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Notas técnicas de SccCreateSubProject y SccGetParentProjectPath
 La adición de soluciones y proyectos al control de código fuente se ha simplificado en Visual Studio para minimizar el número de veces que se solicita al usuario que seleccione ubicaciones en el sistema de control de código fuente. Estos cambios se activan mediante Visual Studio si un complemento de control de código fuente admite las dos funciones nuevas, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) y la `SccGetParentProjectPath` función . Sin embargo, se puede usar la siguiente entrada del Registro para deshabilitar estos cambios y revertir al comportamiento anterior de Visual Studio (API del complemento de control de código fuente versión 1.1):

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Si esta entrada del Registro no existe o está establecida en dword:000000000, Visual Studio intenta usar las nuevas funciones y `SccCreateSubProject` `SccGetParentProjectPath` .

 Si la entrada del Registro se establece en dword:00000001, Visual Studio no intenta usar estas nuevas funciones y las operaciones de agregar al control de código fuente funcionan como lo hacían en versiones anteriores de Visual Studio.

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
