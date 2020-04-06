---
title: Función SccInitialize (SccInitialize) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700640"
---
# <a name="sccinitialize-function"></a>SccInitialize (Función)
Esta función inicializa el complemento de control de código fuente y proporciona capacidades y límites al entorno de desarrollo integrado (IDE).

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

[en] El complemento de control de código fuente puede colocar un puntero a su estructura de contexto aquí.

 `hWnd`

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 `lpCallerName`

[en] El nombre del programa que llama al complemento de control de código fuente.

 `lpSccName`

[adentro, fuera] El búfer donde el complemento de control de código `SCC_NAME_LEN`fuente coloca su propio nombre (no debe superar).

 `lpSccCaps`

[fuera] Devuelve los indicadores de capacidad del complemento de control de código fuente.

 `lpAuxPathLabel`

[adentro, fuera] El búfer donde el complemento de control de código `lpAuxProjPath` fuente coloca una cadena que describe el parámetro devuelto `SCC_AUXLABEL_LEN`por [SccOpenProject](../extensibility/sccopenproject-function.md) y [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (no superar).

 `pnCheckoutCommentLen`

[fuera] Devuelve la longitud máxima permitida para un comentario de pago.

 `pnCommentLen`

[fuera] Devuelve la longitud máxima permitida para otros comentarios.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La inicialización del control de código fuente se realizó correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar la operación especificada.|
|SCC_E_NONSPECFICERROR|Error inespecífico; sistema de control de código fuente no se inicializó.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta función cuando carga por primera vez el complemento de control de código fuente. Permite al IDE pasar cierta información, como el nombre del autor de la llamada, al complemento. El IDE también recupera cierta información, como la longitud máxima permitida para los comentarios y las capacidades del complemento.

 Apunta `ppvContext` a `NULL` un puntero. El complemento de control de código fuente puede asignar una estructura `ppvContext`para su propio uso y almacenar un puntero a esa estructura en . El IDE pasará este puntero a todas las demás funciones de la API de VSSCI, lo que permite que el complemento tenga información de contexto disponible sin recurrir al almacenamiento global y admitir varias instancias del complemento. Esta estructura debe desasignarse cuando se llama [a SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Los `lpCallerName` `lpSccName` parámetros y permiten que el IDE y el complemento de control de código fuente intercambien nombres. Estos nombres se pueden utilizar simplemente para distinguir entre varias instancias, o pueden aparecer en menús o cuadros de diálogo.

 El `lpAuxPathLabel` parámetro es una cadena que se utiliza como comentario para identificar la ruta de acceso del proyecto auxiliar que se almacena en el archivo de solución y se pasa al complemento de control de código fuente en una llamada a [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]utiliza la cadena "SourceSafe Project:"; otros complementos de control de código fuente deben abstenerse de usar esta cadena en particular.

 El `lpSccCaps` parámetro proporciona al complemento de control de código fuente un lugar para almacenar bitflags que indican las capacidades del complemento. (Para obtener una lista completa de indicadores de bits de capacidad, consulte [Indicadores](../extensibility/capability-flags.md)de capacidad ). Por ejemplo, si el complemento planea escribir resultados en una función de devolución de llamada proporcionada por el autor de la llamada, el complemento establecería el bit de capacidad SCC_CAP_TEXTOUT. Esto indicaría que el IDE crea una ventana para los resultados del control de versiones.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Marcas de capacidad](../extensibility/capability-flags.md)
