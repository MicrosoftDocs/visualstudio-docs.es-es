---
title: Función SccRunScc (SccRunScc) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700406"
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

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 nArchivos

[en] Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

[en] Matriz de nombres de archivo seleccionados.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La herramienta de administración del control de código fuente se invocó correctamente.|
|SCC_I_OPERATIONCANCELED|La operación fue cancelada.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema de control de código fuente.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención.|
|SCC_E_CONNECTIONFAILURE|No se pudo conectar al sistema de control de código fuente.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 Esta función permite al autor de la llamada acceder a toda la gama de características del sistema de control de código fuente a través de una herramienta de administración externa. Si el sistema de control de código fuente no tiene interfaz de usuario, el complemento de control de código fuente puede implementar una interfaz para realizar las funciones de administración necesarias.

 Esta función se llama con un recuento y una matriz de nombres de archivo para los archivos seleccionados actualmente. Si la herramienta de administración lo admite, la lista de archivos se puede utilizar para preseleccionar archivos en la interfaz de administración; de lo contrario, la lista puede ser ignorada.

 Esta función se invoca normalmente cuando el usuario selecciona la **>Iniciar \<servidor** de Control de código fuente en **el** -> menú**Control de código fuente** de archivos. Esta opción del menú **Inicio** siempre se puede deshabilitar o incluso ocultar estableciendo una entrada del Registro. Consulte [Cómo: Instalar un complemento](../extensibility/internals/how-to-install-a-source-control-plug-in.md) de Control de código fuente para obtener más información. Esta función solo se llama `SCC_CAP_RUNSCC` si [SccInitialize](../extensibility/sccinitialize-function.md) devuelve el bit de capacidad (consulte [Indicadores](../extensibility/capability-flags.md) de capacidad para obtener más información sobre este y otros bits de capacidad).

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Instalación de un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Marcas de capacidad](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
