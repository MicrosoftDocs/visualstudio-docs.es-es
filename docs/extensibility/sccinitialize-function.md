---
description: Esta función inicializa el complemento de control de código fuente y proporciona funcionalidades y límites al entorno de desarrollo integrado (IDE).
title: SccInitialize Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 633e8909febd758df455a9375f735a93e3407c77
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902532"
---
# <a name="sccinitialize-function"></a>SccInitialize (Función)
Esta función inicializa el complemento de control de código fuente y proporciona funcionalidades y límites al entorno de desarrollo integrado (IDE).

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

[in] El complemento de control de código fuente puede colocar aquí un puntero a su estructura de contexto.

 `hWnd`

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 `lpCallerName`

[in] Nombre del programa que llama al complemento de control de código fuente.

 `lpSccName`

[in, out] Búfer donde el complemento de control de código fuente coloca su propio nombre (no para superar `SCC_NAME_LEN` ).

 `lpSccCaps`

[out] Devuelve las marcas de funcionalidad del complemento de control de código fuente.

 `lpAuxPathLabel`

[in, out] Búfer donde el complemento de control de código fuente coloca una cadena que describe el parámetro devuelto por `lpAuxProjPath` [SccOpenProject](../extensibility/sccopenproject-function.md) y [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (no para superar `SCC_AUXLABEL_LEN` ).

 `pnCheckoutCommentLen`

[out] Devuelve la longitud máxima permitida para un comentario de finalización de la compra.

 `pnCommentLen`

[out] Devuelve la longitud máxima permitida para otros comentarios.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La inicialización del control de código fuente se ha realiza correctamente.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar la operación especificada.|
|SCC_E_NONSPECFICERROR|Error no específico; no se inicializó el sistema de control de código fuente.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta función cuando carga por primera vez el complemento de control de código fuente. Permite que el IDE pase cierta información, como el nombre del autor de la llamada, al complemento. El IDE también obtiene cierta información, como la longitud máxima permitido para los comentarios y las funcionalidades del complemento.

 Apunta `ppvContext` a un `NULL` puntero. El complemento de control de código fuente puede asignar una estructura para su propio uso y almacenar un puntero a esa estructura en `ppvContext` . El IDE pasará este puntero a todas las demás funciones de LA API de VSSCI, lo que permite que el complemento tenga información de contexto disponible sin tener que recurrir al almacenamiento global y admitir varias instancias del complemento. Esta estructura se debe desasignar cuando se llama a [SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Los `lpCallerName` parámetros `lpSccName` y habilitan el IDE y el complemento de control de código fuente para intercambiar nombres. Estos nombres se pueden usar simplemente para distinguir entre varias instancias, o pueden aparecer realmente en menús o cuadros de diálogo.

 El parámetro es una cadena que se usa como comentario para identificar la ruta de acceso del proyecto auxiliar que se almacena en el archivo de solución y se pasa al complemento de control de código fuente en una llamada `lpAuxPathLabel` a [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] usa la cadena "SourceSafe Project:"; otros complementos de control de código fuente deben evitar el uso de esta cadena determinada.

 El parámetro proporciona al complemento de control de código fuente un lugar para almacenar las marcas de `lpSccCaps` bits que indican las funcionalidades del complemento. (Para obtener una lista completa de las marcas de bits de funcionalidad, vea [Marcas de funcionalidad).](../extensibility/capability-flags.md) Por ejemplo, si el complemento planea escribir resultados en una función de devolución de llamada proporcionada por el autor de la llamada, el complemento establecería el bit de funcionalidad SCC_CAP_TEXTOUT. Esto indicaría al IDE que cree una ventana para los resultados del control de versiones.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Marcas de capacidad](../extensibility/capability-flags.md)
