---
title: Función SccRunScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e577af3ce70280b81681cb72295c3511dd3ab4a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720539"
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

 Identificador

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 N archivos

de Número de archivos especificados en la matriz de `lpFileNames`.

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

## <a name="remarks"></a>Comentarios
 Esta función permite que el llamador tenga acceso a toda la gama de características del sistema de control de código fuente a través de una herramienta de administración externa. Si el sistema de control de código fuente no tiene ninguna interfaz de usuario, el complemento de control de código fuente puede implementar una interfaz para realizar las funciones de administración necesarias.

 Se llama a esta función con un recuento y una matriz de nombres de archivo para los archivos seleccionados actualmente. Si la herramienta de administración lo admite, se puede usar la lista de archivos para preseleccionar archivos en la interfaz de administración. de lo contrario, la lista se puede omitir.

 Normalmente, esta función se invoca cuando el usuario selecciona **iniciar \<Source controlar el servidor >** desde el menú **archivo**  -> **control de código fuente** . Esta opción de menú **iniciar** puede estar siempre deshabilitada o incluso oculta mediante la configuración de una entrada del registro. Consulte [Cómo: instalar un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md) para obtener más información. Solo se llama a esta función si [SccInitialize](../extensibility/sccinitialize-function.md) devuelve el bit de funcionalidad `SCC_CAP_RUNSCC` (vea [marcas de funcionalidad](../extensibility/capability-flags.md) para obtener más información sobre este y otros bits de capacidad).

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Instalación de un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Marcadores de capacidad](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)