---
description: Esta función muestra el historial de los archivos especificados.
title: SccHistory Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1208bd0cb13661f1aa60bb9f97c9e4502e517e6d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902545"
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

[in] Estructura de contexto del complemento de control de código fuente.

 `hWnd`

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 `nFiles`

[in] Número de archivos especificados en la `lpFileName` matriz.

 `lpFileName`

[in] Matriz de nombres completos de archivos.

 `fOptions`

[in] Marcas de comandos (actualmente no se usan).

 `pvOptions`

[in] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El historial de versiones se obtuvo correctamente.|
|SCC_I_RELOADFILE|El sistema de control de código fuente modificó realmente el archivo en el disco al capturar el historial (por ejemplo, obteniendo una versión anterior del mismo), por lo que el IDE debe volver a cargar este archivo.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_PROJNOTOPEN|El proyecto no se ha abierto.|
|SCC_E_NONSPECIFICERROR|Error no específico. No se pudo obtener el historial de archivos.|

## <a name="remarks"></a>Observaciones
 El complemento de control de código fuente puede mostrar su propio cuadro de diálogo para mostrar el historial de cada archivo, utilizando `hWnd` como ventana primaria. Como alternativa, se puede usar la función de devolución de llamada de salida de texto opcional proporcionada a [SccOpenProject,](../extensibility/sccopenproject-function.md) si se admite.

 Tenga en cuenta que, en determinadas circunstancias, el archivo que se está examinando puede cambiar durante la ejecución de esta llamada. Por ejemplo, el comando history ofrece al usuario la oportunidad [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] de obtener una versión anterior del archivo. En tal caso, el complemento de control de código fuente vuelve para advertir al IDE de que necesita volver a `SCC_I_RELOAD` cargar el archivo.

> [!NOTE]
> Si el complemento de control de código fuente no admite esta función para una matriz de archivos, solo se puede mostrar el historial de archivos para el primer archivo.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
