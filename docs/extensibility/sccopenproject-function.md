---
description: Esta función abre un proyecto de control de código fuente existente o crea uno nuevo.
title: Función SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1326319b483aa707b77e0d7142d816b01fc7d3b1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902402"
---
# <a name="sccopenproject-function"></a>SccOpenProject (Función)
Esta función abre un proyecto de control de código fuente existente o crea uno nuevo.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] Nombre del usuario (que no debe superar SCC_USER_SIZE, incluido el terminador NULL).

 lpProjName

[in] Cadena que identifica el nombre del proyecto.

 lpLocalProjPath

[in] Ruta de acceso a la carpeta de trabajo del proyecto.

 lpProjPath

[in, out] Cadena auxiliar opcional que identifica el proyecto (que no debe superar SCC_AUXPATH_SIZE, incluido el terminador NULL).

 lpComment

[in] Comente un nuevo proyecto que se está creando.

 lpTextOutProc

[in] Función de devolución de llamada opcional para mostrar la salida de texto desde el complemento de control de código fuente.

 dwFlags

[in] Indica si es necesario crear un nuevo proyecto si el proyecto es desconocido para el complemento de control de código fuente. El valor puede ser una combinación de `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Se ha abierto correctamente el proyecto.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el sistema de control de código fuente.|
|SCC_E_COULDNOTCREATEPROJECT|El proyecto no existía antes de la llamada;  se `SCC_OPT_CREATEIFNEW` estableció la marca , pero no se pudo crear el proyecto.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_UNKNOWNPROJECT|El proyecto es desconocido para el complemento de control de código fuente y no `SCC_OPT_CREATEIFNEW` se estableció la marca .|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o inutilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECFICERROR|Un error no específico; No se inicializó el sistema de control de código fuente.|

## <a name="remarks"></a>Observaciones
 El IDE puede pasar un nombre de usuario ( ) o simplemente pasar `lpUser` un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de código fuente debe usarlo como valor predeterminado. Sin embargo, si no se ha pasado ningún nombre o si se ha registrado un error en el inicio de sesión con el nombre especificado, el complemento debe pedir al usuario que inicie sesión y devolverá el nombre válido en cuando reciba un inicio de sesión válido Porque el complemento puede cambiar la cadena de nombre de usuario, el IDE siempre asignará un búfer de tamaño `lpUser` `.` ( +1 o SCC_USER_SIZE, que incluye espacio para el terminador `SCC_USER_LEN` null).

> [!NOTE]
> La primera acción que puede ser necesaria para realizar el IDE puede ser una llamada a la `SccOpenProject` función o [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Por esta razón, ambos tienen un parámetro `lpUser` idéntico.

 `lpAuxProjPath` y `lpProjName` se leen desde el archivo de solución, o se devuelven desde una llamada a la `SccGetProjPath` función . Estos parámetros contienen las cadenas que el complemento de control de código fuente asocia al proyecto y solo son significativos para el complemento. Si no hay ninguna de estas cadenas en el archivo de solución y no se ha pida al usuario que examine (lo que devolvería una cadena a través de la función ), el IDE pasa cadenas vacías para y , y espera que el complemento actualice estos valores cuando esta función `SccGetProjPath` `lpAuxProjPath` `lpProjName` vuelva.

 `lpTextOutProc` es un puntero a una función de devolución de llamada proporcionada por el IDE al complemento de control de código fuente con el fin de mostrar la salida del resultado del comando. Esta función de devolución de llamada se describe en detalle en [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Si el complemento de control de código fuente pretende aprovechar esta ventaja, debe haber establecido la marca en `SCC_CAP_TEXTOUT` [SccInitialize](../extensibility/sccinitialize-function.md). Si no se estableció esa marca o si el IDE no admite esta característica, `lpTextOutProc` será `NULL` .

 El `dwFlags` parámetro controla el resultado en caso de que el proyecto que se abre no exista actualmente. Consta de dos puntos de bits y `SCC_OP_CREATEIFNEW` `SCC_OP_SILENTOPEN` . Si el proyecto que se está abierto ya existe, la función simplemente abre el proyecto y devuelve `SCC_OK` . Si el proyecto no existe y si la marca está en, el complemento de control de código fuente puede crear el proyecto en el sistema de control de código fuente, abrirlo `SCC_OP_CREATEIFNEW` y devolver `SCC_OK` . Si el proyecto no existe y la marca está desactivada, el complemento debe comprobar `SCC_OP_CREATEIFNEW` la `SCC_OP_SILENTOPEN` marca. Si esa marca no está en, el complemento puede solicitar al usuario un nombre de proyecto. Si esa marca está en, el complemento simplemente debe devolver `SCC_E_UNKNOWNPROJECT` .

## <a name="calling-order"></a>Orden de llamada
 En el curso normal de los eventos, primero se llamaría a [SccInitialize](../extensibility/sccinitialize-function.md) para abrir una sesión de control de código fuente. Una sesión puede constar de una llamada a , seguida de otras llamadas a la función de API del complemento de control de código fuente, y finalizará con una llamada `SccOpenProject` a [SccCloseProject](../extensibility/scccloseproject-function.md). Estas sesiones se pueden repetir varias veces antes de llamar a [SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Si el complemento de control de código fuente establece el bit en , la secuencia de sesión anterior se puede repetir `SCC_CAP_REENTRANT` `SccInitialize` muchas veces en paralelo. Las distintas estructuras realiza un seguimiento de las distintas sesiones, en las que cada una está `pvContext` asociada a un proyecto abierto a la `pvContext` vez. Según el parámetro , el complemento puede determinar a qué proyecto se hace `pvContext` referencia en una llamada determinada. Si no se establece el bit de funcionalidad, los complementos de control de código fuente no reentrante están limitados en su capacidad para trabajar `SCC_CAP_REENTRANT` con varios proyectos.

> [!NOTE]
> El `SCC_CAP_REENTRANT` bit se introdujo en la versión 1.1 de la API de complemento de control de código fuente. No se establece ni se omite en la versión 1.0, y se supone que todos los complementos de control de código fuente de la versión 1.0 no son reentrantes.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
