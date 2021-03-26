---
description: Dada una lista de nombres de archivo completos, esta función los desprotege en la unidad local.
title: Función SccCheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f93052ebe255cddb4703a8246b7e89c744548a7f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060385"
---
# <a name="scccheckout-function"></a>SccCheckout función)
Dada una lista de nombres de archivo completos, esta función los desprotege en la unidad local. El comentario se aplica a todos los archivos que se van a desproteger. El argumento comment puede ser una `null` cadena.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parámetros
 pvContext

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 N archivos

de Número de archivos seleccionados para desproteger.

 lpFileNames

de Matriz de nombres de ruta de acceso local completa de los archivos que se van a extraer del repositorio.

 lpComment

de Comentario que se va a aplicar a cada uno de los archivos seleccionados que se van a desproteger.

 Opciones

de Marcas de comandos (vea [marcadores usado por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

de Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La desprotección fue correcta.|
|SCC_E_FILENOTCONTROLLED|El archivo seleccionado no está bajo el control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_NONSPECIFICERROR|Error no específico. No se ha desprotegido el archivo.|
|SCC_E_ALREADYCHECKEDOUT|El usuario ya tiene el archivo desprotegido.|
|SCC_E_FILEISLOCKED|El archivo está bloqueado, lo que prohíbe la creación de nuevas versiones.|
|SCC_E_FILEOUTEXCLUSIVE|Otro usuario ha realizado una desprotección exclusiva en este archivo.|
|SCC_I_OPERATIONCANCELED|La operación se canceló antes de completarse.|

## <a name="see-also"></a>Consulte también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Marcadores usado por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
