---
description: Esta función invoca la herramienta de administración del control de código fuente.
title: Función SccRunScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca492c35ba061072dc9e4b3d0eabc42476bcd8ed
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221371"
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

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 N archivos

de Número de archivos especificados en la `lpFileNames` matriz.

 lpFileNames

de Matriz de nombres de archivo seleccionados.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Se invocó correctamente la herramienta de administración del control de código fuente.|
|SCC_I_OPERATIONCANCELED|La operación se canceló.|
|SCC_E_INITIALIZEFAILED|No se pudo inicializar el sistema de control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención.|
|SCC_E_CONNECTIONFAILURE|No se pudo conectar con el sistema de control de código fuente.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Esta función permite que el llamador tenga acceso a toda la gama de características del sistema de control de código fuente a través de una herramienta de administración externa. Si el sistema de control de código fuente no tiene ninguna interfaz de usuario, el complemento de control de código fuente puede implementar una interfaz para realizar las funciones de administración necesarias.

 Se llama a esta función con un recuento y una matriz de nombres de archivo para los archivos seleccionados actualmente. Si la herramienta de administración lo admite, se puede usar la lista de archivos para preseleccionar archivos en la interfaz de administración. de lo contrario, la lista se puede omitir.

 Normalmente, esta función se invoca cuando el usuario selecciona el **Inicio \<Source Control Server>** desde el   ->  menú **control de código fuente** del archivo. Esta opción de menú **iniciar** puede estar siempre deshabilitada o incluso oculta mediante la configuración de una entrada del registro. Consulte [Cómo: instalar un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md) para obtener más información. Solo se llama a esta función si [SccInitialize](../extensibility/sccinitialize-function.md) devuelve el `SCC_CAP_RUNSCC` bit de funcionalidad (vea [marcas de funcionalidad](../extensibility/capability-flags.md) para obtener más información sobre este y otros bits de capacidad).

## <a name="see-also"></a>Consulte también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Instalación de un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Marcas de capacidad](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
