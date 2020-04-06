---
title: Función SccHistory (SccHistory) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734afefd97e61867076d487acbcf67f10f54e672
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700665"
---
# <a name="scchistory-function"></a>SccHistory (Función)
Esta función muestra el historial de los archivos especificados.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parámetros
 `pvContext`

[en] La estructura de contexto del complemento de control de código fuente.

 `hWnd`

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 `nFiles`

[en] Número de archivos especificados en la `lpFileName` matriz.

 `lpFileName`

[en] Matriz de nombres completos de archivos.

 `fOptions`

[en] Marcas de comando (actualmente no se utilizan).

 `pvOptions`

[en] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El historial de versiones se ha obtenido correctamente.|
|SCC_I_RELOADFILE|El sistema de control de código fuente modificó realmente el archivo en el disco mientras se recupera el historial (por ejemplo, obteniendo una versión antigua del mismo), por lo que el IDE debe volver a cargar este archivo.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_PROJNOTOPEN|El proyecto no se ha abierto.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico. No se pudo obtener el historial de archivos.|

## <a name="remarks"></a>Observaciones
 El complemento de control de código fuente puede mostrar su propio `hWnd` cuadro de diálogo para mostrar el historial de cada archivo, utilizando como la ventana primaria. Como alternativa, se puede utilizar la función de devolución de llamada de salida de texto opcional proporcionada a [SccOpenProject,](../extensibility/sccopenproject-function.md) si se admite.

 Tenga en cuenta que, en determinadas circunstancias, el archivo que se está examinando puede cambiar durante la ejecución de esta llamada. Por ejemplo, [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] el comando history da al usuario la oportunidad de obtener una versión antigua del archivo. En tal caso, el complemento de `SCC_I_RELOAD` control de código fuente vuelve a advertir al IDE que necesita volver a cargar el archivo.

> [!NOTE]
> Si el complemento de control de código fuente no admite esta función para una matriz de archivos, solo se puede mostrar el historial de archivos del primer archivo.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
