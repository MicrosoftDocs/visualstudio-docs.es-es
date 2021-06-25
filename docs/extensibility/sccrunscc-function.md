---
description: Esta función invoca la herramienta de administración del control de código fuente.
title: SccRunScc Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c865931ed52601761f0bd519bf360d584d49ec04
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904118"
---
# <a name="sccrunscc-function"></a>SccRunScc (Función)
Esta función invoca la herramienta de administración del control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nFiles

[in] Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nombres de archivo seleccionados.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La herramienta de administración del control de código fuente se invocó correctamente.|
|SCC_I_OPERATIONCANCELED|La operación se canceló.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema de control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención.|
|SCC_E_CONNECTIONFAILURE|No se pudo conectar al sistema de control de código fuente.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Esta función permite al autor de la llamada acceder a toda la gama de características del sistema de control de código fuente a través de una herramienta de administración externa. Si el sistema de control de código fuente no tiene ninguna interfaz de usuario, el complemento de control de código fuente puede implementar una interfaz para realizar las funciones de administración necesarias.

 Se llama a esta función con un recuento y una matriz de nombres de archivo para los archivos seleccionados actualmente. Si la herramienta de administración la admite, la lista de archivos se puede usar para preseleccionar archivos en la interfaz de administración; De lo contrario, se puede omitir la lista.

 Esta función se invoca normalmente cuando el usuario selecciona **Iniciar en \<Source Control Server>** el menú Control **de** código  ->  **fuente de** archivo. Esta **opción de** menú Iniciar siempre se puede deshabilitar o incluso ocultar estableciendo una entrada del Registro. Consulte [Cómo: Instalar un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md) para obtener más información. Solo se llama a esta función si [SccInitialize](../extensibility/sccinitialize-function.md) devuelve el bit de funcionalidad (consulte Marcas de funcionalidad para obtener más información sobre este y otros `SCC_CAP_RUNSCC` bits de funcionalidad). [](../extensibility/capability-flags.md)

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Instalación de un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Marcas de capacidad](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
