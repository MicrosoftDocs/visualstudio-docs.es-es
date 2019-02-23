---
title: SccUncheckout (función) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6362025f63e4e4f470a7fe107365a59ef99e1e17
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717421"
---
# <a name="sccuncheckout-function"></a>SccUncheckout (Función)
Esta función deshace una operación de desprotección anterior, restaurar, por tanto, el contenido del archivo seleccionado o los archivos al estado anterior a la desprotección. Se pierden todos los cambios realizados en el archivo desde la desprotección.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[in] La estructura de contexto de complemento de control de origen.

 hWnd

[in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.

 nFiles

[in] Número de archivos especificados en el `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nombres de ruta de acceso local completa de los archivos que se va a deshacer una desprotección.

 Opciones

[in] Marcas de comando (no se utiliza).

 pvOptions

[in] Opciones de específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Deshacer desprotección fue correcta.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso el sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Error no específico. Deshacer desprotección no se realizó correctamente.|
|SCC_E_NOTCHECKEDOUT|El usuario no tiene el archivo desprotegido.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_PROJNOTOPEN|No ha abierto el proyecto de control de código fuente.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|

## <a name="remarks"></a>Comentarios
 Después de realizar esta operación, el `SCC_STATUS_CHECKEDOUT` y `SCC_STATUS_MODIFIED` marcas ambos se borrará los archivos en el que se realizó la desprotección.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)