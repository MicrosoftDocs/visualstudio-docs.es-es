---
title: Función SccOpenProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa4a715f8d1b87aa831f6a315f07a19e5d4f46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721052"
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

 Identificador

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 lpUser

[in, out] Nombre del usuario (no debe superar SCC_USER_SIZE, incluido el terminador NULL).

 lpProjName

de Cadena que identifica el nombre del proyecto.

 lpLocalProjPath

de La ruta de acceso a la carpeta de trabajo del proyecto.

 lpAuxProjPath

[in, out] Una cadena auxiliar opcional que identifica el proyecto (no supere SCC_AUXPATH_SIZE, incluido el terminador NULL).

 lpComment

de Comentario a un proyecto nuevo que se va a crear.

 lpTextOutProc

de Función de devolución de llamada opcional para mostrar la salida de texto del complemento de control de código fuente.

 dwFlags

de Indica si es necesario crear un nuevo proyecto si el proyecto es desconocido para el complemento de control de código fuente. El valor puede ser una combinación de `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Éxito al abrir el proyecto.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el proyecto.|
|SCC_E_INVALIDUSER|El usuario no pudo iniciar sesión en el sistema de control de código fuente.|
|SCC_E_COULDNOTCREATEPROJECT|El proyecto no existía antes de la llamada.  se estableció la marca de `SCC_OPT_CREATEIFNEW`, pero no se pudo crear el proyecto.|
|SCC_E_PROJSYNTAXERR|Sintaxis de proyecto no válida.|
|SCC_E_UNKNOWNPROJECT|El proyecto es desconocido para el complemento de control de código fuente y no se ha establecido la marca de `SCC_OPT_CREATEIFNEW`.|
|SCC_E_INVALIDFILEPATH|Ruta de acceso de archivo no válida o no utilizable.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NONSPECFICERROR|Un error no específico; no se inicializó el sistema de control de código fuente.|

## <a name="remarks"></a>Comentarios
 El IDE puede pasar un nombre de usuario (`lpUser`) o simplemente pasar un puntero a una cadena vacía. Si hay un nombre de usuario, el complemento de control de código fuente debe usarlo como valor predeterminado. Sin embargo, si no se ha pasado ningún nombre, o si se produjo un error en el inicio de sesión con el nombre especificado, el complemento debería solicitar al usuario que inicie sesión y devolverá el nombre válido en `lpUser` cuando reciba un inicio de sesión válido `.` porque el complemento puede cambiar la cadena de nombre de usuario. , el IDE asignará siempre un búfer de tamaño (`SCC_USER_LEN` + 1 o SCC_USER_SIZE, que incluye el espacio para el terminador null).

> [!NOTE]
> La primera acción que el IDE puede necesitar realizar puede ser una llamada a la función `SccOpenProject` o a [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Por esta razón, ambos tienen un parámetro `lpUser` idéntico.

 `lpAuxProjPath` y `lpProjName` se leen desde el archivo de solución o se devuelven desde una llamada a la función `SccGetProjPath`. Estos parámetros contienen las cadenas que el complemento de control de código fuente asocia al proyecto y son significativas solo para el complemento. Si no hay cadenas de este tipo en el archivo de solución y no se ha solicitado al usuario que busque (que devolvería una cadena a través de la función `SccGetProjPath`), el IDE pasa cadenas vacías para `lpAuxProjPath` y `lpProjName`, y espera que el complemento actualice estos valores cuando sea is devuelve la función.

 `lpTextOutProc` es un puntero a una función de devolución de llamada proporcionada por el IDE para el complemento de control de código fuente con el fin de mostrar la salida del resultado del comando. Esta función de devolución de llamada se describe en detalle en [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

> [!NOTE]
> Si el complemento de control de código fuente tiene la intención de aprovechar esto, debe haber establecido la marca de `SCC_CAP_TEXTOUT` en [SccInitialize](../extensibility/sccinitialize-function.md). Si no se ha establecido esa marca, o si el IDE no admite esta característica, `lpTextOutProc` se `NULL`.

 El parámetro `dwFlags` controla el resultado en caso de que el proyecto que se está abriendo no exista actualmente. Consta de dos marcadores, `SCC_OP_CREATEIFNEW` y `SCC_OP_SILENTOPEN`. Si el proyecto que se está abriendo ya existe, la función simplemente abre el proyecto y devuelve `SCC_OK`. Si el proyecto no existe y la marca `SCC_OP_CREATEIFNEW` está activada, el complemento de control de código fuente puede crear el proyecto en el sistema de control de código fuente, abrirlo y devolver `SCC_OK`. Si el proyecto no existe, y si la marca de `SCC_OP_CREATEIFNEW` está desactivada, el complemento debe comprobar la marca de `SCC_OP_SILENTOPEN`. Si esa marca no está activada, el complemento puede solicitar al usuario un nombre de proyecto. Si esa marca está activada, el complemento simplemente debe devolver `SCC_E_UNKNOWNPROJECT`.

## <a name="calling-order"></a>Orden de llamada
 En el curso normal de los eventos, se llamaría primero a [SccInitialize](../extensibility/sccinitialize-function.md) para abrir una sesión de control de código fuente. Una sesión puede constar de una llamada a `SccOpenProject`, seguido de otras llamadas a funciones de la API del complemento de control de código fuente y finalizará con una llamada a [SccCloseProject](../extensibility/scccloseproject-function.md). Estas sesiones se pueden repetir varias veces antes de que se llame a [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Si el complemento de control de código fuente establece el bit de `SCC_CAP_REENTRANT` en `SccInitialize`, la secuencia de sesión anterior se puede repetir muchas veces en paralelo. Las distintas estructuras de `pvContext` realizan el seguimiento de las distintas sesiones, en las que cada `pvContext` se asocia a un proyecto abierto cada vez. Basándose en el parámetro `pvContext`, el complemento puede determinar a qué proyecto se hace referencia en una llamada determinada. Si no se establece el bit de funcionalidad `SCC_CAP_REENTRANT`, los complementos de control de código fuente de nonreentrant se limitan en su capacidad de trabajar con varios proyectos.

> [!NOTE]
> El bit de `SCC_CAP_REENTRANT` se presentó en la versión 1,1 de la API del complemento de control de código fuente. No se establece o se omite en la versión 1,0, y se supone que todos los complementos de control de código fuente de la versión 1,0 son nonreentrant.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Restricciones en las longitudes de cadena](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)