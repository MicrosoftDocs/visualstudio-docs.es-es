---
description: Esta función muestra (o opcionalmente solo comprueba) las diferencias entre el archivo actual (en el disco local) y su última versión de check-in en el sistema de control de código fuente.
title: SccDiff Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 484d8b5e988ede9b50099e3c0376f2c3afce8317
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904661"
---
# <a name="sccdiff-function"></a>Función SccDiff
Esta función muestra (o opcionalmente solo comprueba) las diferencias entre el archivo actual (en el disco local) y su última versión de check-in en el sistema de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parámetros
 pvContext

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpFileName

[in] Nombre de archivo para el que se solicita la diferencia.

 fOptions

[in] Marcas de comandos. Para obtener información detallada, vea la sección Comentarios de.

 pvOptions

[in] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La copia de trabajo y la versión del servidor son idénticas.|
|SCC_I_FILESDIFFERS|La copia de trabajo difiere de la versión bajo control de código fuente.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Error no específico; no se obtuvo la diferencia de archivo.|
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|

## <a name="remarks"></a>Observaciones
 Esta función tiene dos propósitos diferentes. De forma predeterminada, muestra una lista de cambios en un archivo. El complemento de control de código fuente abre su propia ventana, en el formato que elija, para mostrar las diferencias entre el archivo del usuario en disco y la versión más reciente del archivo bajo control de código fuente.

 Como alternativa, es posible que el IDE simplemente tenga que determinar si un archivo ha cambiado. Por ejemplo, es posible que el IDE tenga que determinar si es seguro des check-out de un archivo sin informar al usuario. En ese caso, el IDE pasa la `SCC_DIFF_CONTENTS` marca . El complemento de control de código fuente debe comprobar el archivo en disco, byte a byte, en el archivo controlado por código fuente y devolver un valor que indica si los dos archivos son diferentes sin mostrar nada al usuario.

 Como optimización del rendimiento, el complemento de control de código fuente puede usar una alternativa basada en una suma de comprobación o una marca de tiempo en lugar de la comparación byte a byte llamada por : estas formas de comparación son obviamente más rápidas pero menos `SCC_DIFF_CONTENTS` confiables. No todos los sistemas de control de código fuente pueden admitir estos métodos de comparación alternativos y es posible que el complemento tenga que volver a una comparación de contenido. Como mínimo, todos los complementos de control de código fuente deben admitir una comparación de contenido.

> [!NOTE]
> Las marcas de diferencia rápida son mutuamente excluyentes. Es válido no pasar ninguna marca, pero no es válido pasar simultáneamente más de una. `SCC_DIFF_QUICK_DIFF`, que es una máscara que combina todas las marcas, se puede usar para probar, pero nunca debe pasarse como parámetro.

|`fOption`|Significado|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Comparación sin diferencias entre mayúsculas y minúsculas (se puede usar para diferencias rápidas o visuales).|
|SCC_DIFF_IGNORESPACE|Omite el espacio en blanco (se puede usar para diferencias rápidas o visuales).|
|SCC_DIFF_QD_CONTENTS|Compara de forma silenciosa el archivo, byte por byte.|
|SCC_DIFF_QD_CHECKSUM|Compara silenciosamente el archivo a través de una suma de comprobación cuando se admite. Si no se admite, vuelve a una comparación de contenido.|
|SCC_DIFF_QD_TIME|Compara silenciosamente el archivo a través de su marca de tiempo cuando se admite. Si no se admite, vuelve a una comparación de contenido.|

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
