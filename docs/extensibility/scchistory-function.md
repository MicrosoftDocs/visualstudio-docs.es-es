---
description: Esta función muestra el historial de los archivos especificados.
title: Función SccHistory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 11a3056e34d15e2e04b687a518e86041dc270997
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063856"
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

de Estructura de contexto del complemento de control de código fuente.

 `hWnd`

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 `nFiles`

de Número de archivos especificados en la `lpFileName` matriz.

 `lpFileName`

de Matriz de los nombres completos de los archivos.

 `fOptions`

de Marcas de comando (actualmente no utilizadas).

 `pvOptions`

de Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El historial de versiones se obtuvo correctamente.|
|SCC_I_RELOADFILE|El sistema de control de código fuente modificó realmente el archivo en el disco mientras se recuperaba el historial (por ejemplo, al obtener una versión anterior), por lo que el IDE debe volver a cargar este archivo.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_OPNOTSUPPORTED|El sistema de control de código fuente no admite esta operación.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_PROJNOTOPEN|No se ha abierto el proyecto.|
|SCC_E_NONSPECIFICERROR|Error no específico. No se pudo obtener el historial de archivos.|

## <a name="remarks"></a>Observaciones
 El complemento de control de código fuente puede mostrar su propio cuadro de diálogo para mostrar el historial de cada archivo, usando `hWnd` como ventana primaria. Como alternativa, se puede usar la función de devolución de llamada de salida de texto opcional proporcionada a [SccOpenProject](../extensibility/sccopenproject-function.md) , si es compatible.

 Tenga en cuenta que, en determinadas circunstancias, el archivo que se está examinando puede cambiar durante la ejecución de esta llamada. Por ejemplo, el [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] comando de historial ofrece al usuario una oportunidad para obtener una versión anterior del archivo. En tal caso, el complemento de control de código fuente devuelve `SCC_I_RELOAD` para advertir al IDE de que debe volver a cargar el archivo.

> [!NOTE]
> Si el complemento de control de código fuente no admite esta función para una matriz de archivos, solo se puede mostrar el historial de archivos del primer archivo.

## <a name="see-also"></a>Consulte también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
