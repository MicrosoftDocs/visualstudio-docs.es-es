---
title: Función SccOpenProject ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700568"
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

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[adentro, fuera] El nombre del usuario (no debe superar SCC_USER_SIZE, incluido el terminador NULL).

 lpProjName

[en] Cadena que identifica el nombre del proyecto.

 lpLocalProjPath

[en] La ruta de acceso a la carpeta de trabajo para el proyecto.

 lpAuxProjPath

[adentro, fuera] Una cadena auxiliar opcional que identifica el proyecto (no debe superar SCC_AUXPATH_SIZE, incluido el terminador NULL).

 lpComment

[en] Comentar un nuevo proyecto que se está creando.

 lpTextOutProc

[en] Una función de devolución de llamada opcional para mostrar la salida de texto desde el complemento de control de código fuente.

 dwFlags

[en] Indica si es necesario crear un nuevo proyecto si el proyecto es desconocido para el complemento de control de código fuente. El valor puede `SCC_OP_CREATEIFNEW` ser una combinación de y`SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El éxito en la apertura del proyecto.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el sistema de control de código fuente.|
|SCC_E_COULDNOTCREATEPROJECT|El proyecto no existía antes de la llamada;  se `SCC_OPT_CREATEIFNEW` estableció la bandera, pero no se pudo crear el proyecto.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_UNKNOWNPROJECT|El proyecto es desconocido para el complemento `SCC_OPT_CREATEIFNEW` de control de código fuente y el indicador no se estableció.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o inutilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECFICERROR|Un error inespecífico; el sistema de control de código fuente no se inicializó.|

## <a name="remarks"></a>Observaciones
 El IDE puede pasar un`lpUser`nombre de usuario ( ), o simplemente puede pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de código fuente debe usarlo como valor predeterminado. Sin embargo, si no se pasó ningún nombre, o si el inicio de sesión falló con `lpUser` el nombre dado,`.` el complemento debe solicitar al usuario que inicie sesión y devolverá el nombre válido cuando reciba un inicio de sesión válido Porque el complemento puede cambiar la cadena de nombre de usuario, el IDE siempre asignará un búfer de tamaño (`SCC_USER_LEN`+1 o SCC_USER_SIZE, que incluye espacio para el terminador nulo).

> [!NOTE]
> La primera acción que puede ser necesaria que el `SccOpenProject` IDE realice puede ser una llamada a la función o [sccGetProjPath](../extensibility/sccgetprojpath-function.md). Por esta razón, ambos tienen `lpUser` un parámetro idéntico.

 `lpAuxProjPath`y`lpProjName` se leen desde el archivo de solución, o se devuelven de una llamada a la `SccGetProjPath` función. Estos parámetros contienen las cadenas que el complemento de control de código fuente asocia con el proyecto y son significativas solo para el complemento. Si no hay tales cadenas en el archivo de solución y no se `SccGetProjPath` ha pedido al usuario que examine `lpAuxProjPath` `lpProjName`(que devolvería una cadena a través de la función), el IDE pasa cadenas vacías para ambos y , y espera que el complemento actualice estos valores cuando se devuelva esta función.

 `lpTextOutProc`es un puntero a una función de devolución de llamada proporcionada por el IDE al complemento de control de código fuente con el fin de mostrar la salida de resultado del comando. Esta función de devolución de llamada se describe en detalle en [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Si el complemento de control de código fuente tiene la `SCC_CAP_TEXTOUT` intención de aprovechar esto, debe haber establecido la marca en [el SccInitialize](../extensibility/sccinitialize-function.md). Si no se ha establecido esa marca, o `lpTextOutProc` si `NULL`el IDE no admite esta característica, será .

 El `dwFlags` parámetro controla el resultado en caso de que el proyecto que se está abrindo no exista actualmente. Consta de dos bitflags, `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN`. Si el proyecto que se está abrindo ya `SCC_OK`existe, la función simplemente abre el proyecto y devuelve . Si el proyecto no existe `SCC_OP_CREATEIFNEW` y la marca está activada, el complemento de control de código fuente `SCC_OK`puede crear el proyecto en el sistema de control de código fuente, abrirlo y devolver . Si el proyecto no existe, `SCC_OP_CREATEIFNEW` y si la marca está desactivada, `SCC_OP_SILENTOPEN` el complemento debe comprobar la marca. Si esa marca no está activada, el complemento puede solicitar al usuario un nombre de proyecto. Si esa marca está activada, el `SCC_E_UNKNOWNPROJECT`complemento simplemente debe devolver .

## <a name="calling-order"></a>Orden de llamada
 En el curso normal de los eventos, el [SccInitialize](../extensibility/sccinitialize-function.md) se llamaría primero para abrir una sesión de control de código fuente. Una sesión puede consistir en una llamada a `SccOpenProject`, seguida de otras llamadas a la función de complemento de Control de código fuente y finalizará con una llamada a [SccCloseProject](../extensibility/scccloseproject-function.md). Estas sesiones pueden repetirse varias veces antes de que se llame a [SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Si el complemento de control `SCC_CAP_REENTRANT` de `SccInitialize`código fuente establece el bit en , la secuencia de sesión anterior puede repetirse muchas veces en paralelo. Diferentes `pvContext` estructuras realizan un seguimiento `pvContext` de las diferentes sesiones, en las que cada una está asociada a un proyecto abierto a la vez. Según`pvContext` el parámetro, el complemento puede determinar a qué proyecto se hace referencia en cualquier llamada determinada. Si no `SCC_CAP_REENTRANT` se establece el bit de capacidad, los complementos de control de código fuente no reentrantes están limitados en su capacidad para trabajar con varios proyectos.

> [!NOTE]
> El `SCC_CAP_REENTRANT` bit se introdujo en la versión 1.1 de la API de complemento de Control de código fuente. No se establece o se omite en la versión 1.0, y se supone que todos los complementos de control de código fuente de la versión 1.0 no son reentrantes.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
