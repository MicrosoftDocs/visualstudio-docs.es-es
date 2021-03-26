---
description: Esta función abre un proyecto de control de código fuente existente o crea uno nuevo.
title: Función SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: baada63e84e95fd466e0e5640c592dfe303d8e1a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063765"
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

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] Nombre del usuario (no debe superar SCC_USER_SIZE, incluido el terminador nulo).

 lpProjName

de Cadena que identifica el nombre del proyecto.

 lpLocalProjPath

de La ruta de acceso a la carpeta de trabajo del proyecto.

 lpAuxProjPath

[in, out] Cadena auxiliar opcional que identifica el proyecto (no debe superar SCC_AUXPATH_SIZE, incluido el terminador NULL).

 lpComment

de Comentario a un proyecto nuevo que se va a crear.

 lpTextOutProc

de Función de devolución de llamada opcional para mostrar la salida de texto del complemento de control de código fuente.

 dwFlags

de Indica si es necesario crear un nuevo proyecto si el proyecto es desconocido para el complemento de control de código fuente. El valor puede ser una combinación de `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Éxito al abrir el proyecto.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el sistema de control de código fuente.|
|SCC_E_COULDNOTCREATEPROJECT|El proyecto no existía antes de la llamada.  `SCC_OPT_CREATEIFNEW` se estableció la marca, pero no se pudo crear el proyecto.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_UNKNOWNPROJECT|El proyecto es desconocido para el complemento de control de código fuente y `SCC_OPT_CREATEIFNEW` no se ha establecido la marca.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o no utilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NONSPECFICERROR|Un error no específico; no se inicializó el sistema de control de código fuente.|

## <a name="remarks"></a>Observaciones
 El IDE puede pasar un nombre de usuario ( `lpUser` ) o simplemente pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de código fuente debe usarlo como valor predeterminado. Sin embargo, si no se ha pasado ningún nombre, o si se ha producido un error en el inicio de sesión con el nombre especificado, el complemento debería solicitar al usuario que inicie sesión y devolverá el nombre válido en `lpUser` cuando reciba un inicio de sesión válido `.` porque el complemento puede cambiar la cadena de nombre de usuario, el IDE siempre asignará un búfer de tamaño ( `SCC_USER_LEN` + 1 o SCC_USER_SIZE, que

> [!NOTE]
> La primera acción que el IDE puede necesitar realizar puede ser una llamada a la `SccOpenProject` función o a [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Por esta razón, ambos tienen un `lpUser` parámetro idéntico.

 `lpAuxProjPath` y `lpProjName` se leen desde el archivo de solución o se devuelven desde una llamada a la `SccGetProjPath` función. Estos parámetros contienen las cadenas que el complemento de control de código fuente asocia al proyecto y son significativas solo para el complemento. Si no hay cadenas de este tipo en el archivo de solución y no se ha solicitado al usuario que busque (que devolvería una cadena a través de la `SccGetProjPath` función), el IDE pasa cadenas vacías para `lpAuxProjPath` y `lpProjName` , y espera que el complemento actualice estos valores cuando esta función devuelve un valor.

 `lpTextOutProc` es un puntero a una función de devolución de llamada proporcionada por el IDE para el complemento de control de código fuente con el fin de mostrar la salida del resultado del comando. Esta función de devolución de llamada se describe en detalle en [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Si el complemento de control de código fuente tiene la intención de aprovechar esto, debe haber establecido la `SCC_CAP_TEXTOUT` marca en [SccInitialize](../extensibility/sccinitialize-function.md). Si no se ha establecido esa marca, o si el IDE no admite esta característica, `lpTextOutProc` será `NULL` .

 El `dwFlags` parámetro controla el resultado en caso de que el proyecto que se está abriendo no exista actualmente. Consta de dos marcadores, `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN` . Si el proyecto que se está abriendo ya existe, la función simplemente abre el proyecto y devuelve `SCC_OK` . Si el proyecto no existe y la `SCC_OP_CREATEIFNEW` marca está activada, el complemento de control de código fuente puede crear el proyecto en el sistema de control de código fuente, abrirlo y devolverlo `SCC_OK` . Si el proyecto no existe, y si la `SCC_OP_CREATEIFNEW` marca está desactivada, el complemento debe comprobar la `SCC_OP_SILENTOPEN` marca. Si esa marca no está activada, el complemento puede solicitar al usuario un nombre de proyecto. Si esa marca está activada, el complemento simplemente debe devolver `SCC_E_UNKNOWNPROJECT` .

## <a name="calling-order"></a>Orden de llamada
 En el curso normal de los eventos, se llamaría primero a [SccInitialize](../extensibility/sccinitialize-function.md) para abrir una sesión de control de código fuente. Una sesión puede constar de una llamada a `SccOpenProject` , seguida de otras llamadas a funciones de la API del complemento de control de código fuente y finalizará con una llamada a [SccCloseProject](../extensibility/scccloseproject-function.md). Estas sesiones se pueden repetir varias veces antes de que se llame a [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Si el complemento de control de código fuente establece el `SCC_CAP_REENTRANT` bit en `SccInitialize` , la secuencia de sesión anterior se puede repetir muchas veces en paralelo. Distintas `pvContext` estructuras realizan el seguimiento de las distintas sesiones, en las que cada `pvContext` una está asociada a un proyecto abierto a la vez. Basándose en el `pvContext` parámetro, el complemento puede determinar a qué proyecto se hace referencia en una llamada determinada. Si no se establece el bit de capacidad `SCC_CAP_REENTRANT` , los complementos de control de código fuente de nonreentrant se limitan en su capacidad de trabajar con varios proyectos.

> [!NOTE]
> El `SCC_CAP_REENTRANT` bit se presentó en la versión 1,1 de la API del complemento de control de código fuente. No se establece o se omite en la versión 1,0, y se supone que todos los complementos de control de código fuente de la versión 1,0 son nonreentrant.

## <a name="see-also"></a>Consulte también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
