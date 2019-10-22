---
title: SccInitialize (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a855ecbc65211234b29808fc9e4cf256cd6b25f7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353583"
---
# <a name="sccinitialize-function"></a>SccInitialize (Función)
Esta función inicializa el complemento de control de código fuente y proporciona capacidades y los límites para el entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Parámetros
 `ppvContext`

[in] El complemento de control de código fuente puede colocar un puntero a su estructura de contexto aquí.

 `hWnd`

[in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.

 `lpCallerName`

[in] El nombre de la llamada del control de código fuente complemento del programa.

 `lpSccName`

[in, out] El búfer donde el complemento de control de código fuente coloca su propio nombre (no debe superar los `SCC_NAME_LEN`).

 `lpSccCaps`

[out] Devuelve el control de código fuente de marcadores de capacidad del complemento.

 `lpAuxPathLabel`

[in, out] El búfer donde el complemento de control de código fuente coloca una cadena que describe el `lpAuxProjPath` parámetro devuelto por la [SccOpenProject](../extensibility/sccopenproject-function.md) y [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (no debe superar los `SCC_AUXLABEL_LEN`).

 `pnCheckoutCommentLen`

[out] Devuelve la longitud máxima permitida para un comentario de desprotección.

 `pnCommentLen`

[out] Devuelve la longitud máxima permitida para los demás comentarios.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Inicialización del control de origen se realizó correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar la operación especificada.|
|SCC_E_NONSPECFICERROR|Error no específico; no se inicializó el sistema de control de código fuente.|

## <a name="remarks"></a>Comentarios
 El IDE llama a esta función cuando se carga primero el complemento de control de código fuente. Permite que el IDE pasar cierta información, como el nombre del llamador, el complemento. El IDE también obtiene cierta información como la longitud máxima permitida para los comentarios y capacidades del complemento.

 El `ppvContext` apunta a un `NULL` puntero. Puede asignar una estructura para su propio uso y almacenar un puntero a esa estructura en el complemento de control de código fuente `ppvContext`. El IDE pasará este puntero para cada función de API VSSCI, lo que permite el complemento para tener información de contexto disponible sin tener que recurrir a almacenamiento global y para admitir varias instancias del complemento. Esta estructura debe desasignarse cuando la [SccUninitialize](../extensibility/sccuninitialize-function.md) se llama.

 El `lpCallerName` y `lpSccName` parámetros permiten el IDE y el complemento de control de código fuente intercambiar los nombres. Estos nombres se pueden utilizar simplemente para distinguir entre varias instancias o realmente pueden aparecer en los menús o cuadros de diálogo.

 El `lpAuxPathLabel` parámetro es una cadena que se usa como un comentario para identificar la ruta de acceso de proyecto auxiliar que se almacena en el archivo de solución y pasa el control de código fuente del complemento en una llamada a la [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] usa la cadena "proyecto de SourceSafe:"; otros complementos de control de código fuente deben evitar usar esta cadena concreta.

 El `lpSccCaps` parámetro proporciona el control de código fuente complemento un lugar para almacenar los marcadores de bits que indica las capacidades del complemento. (Para obtener una lista completa de los marcadores de bits de funcionalidad, consulte [marcadores de capacidad](../extensibility/capability-flags.md)). Por ejemplo, si los planes para escribir los resultados a una función de devolución de llamada proporcionada por el autor de llamada, el complemento establecería la capacidad de complemento bit SCC_CAP_TEXTOUT. Esto podría indicar el IDE para crear una ventana de resultados de control de versión.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Marcadores de capacidad](../extensibility/capability-flags.md)