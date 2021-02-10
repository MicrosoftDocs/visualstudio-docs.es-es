---
title: Función SccDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ff2b2d5e5a0043cde17fecd2d59c084d2958e32
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943119"
---
# <a name="sccdiff-function"></a>SccDiff función)
Esta función muestra (u opcionalmente solo comprueba las diferencias entre el archivo actual (en el disco local) y su última versión protegida en el sistema de control de código fuente.

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

de Estructura de contexto del complemento de control de código fuente.

 hWnd

de Identificador de la ventana del IDE que el complemento de control de código fuente puede utilizar como elemento primario para los cuadros de diálogo que proporciona.

 lpFileName

de Nombre de archivo para el que se solicita la diferencia.

 Opciones

de Marcas de comandos. Para obtener información detallada, vea la sección Comentarios de.

 pvOptions

de Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La copia de trabajo y la versión del servidor son idénticas.|
|SCC_I_FILESDIFFERS|La copia de trabajo difiere de la versión bajo control de código fuente.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_NOTAUTHORIZED|El usuario no tiene permiso para realizar esta operación.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Error no específico; no se obtuvo la diferencia de archivos.|
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|

## <a name="remarks"></a>Notas
 Esta función tiene dos fines diferentes. De forma predeterminada, se muestra una lista de cambios en un archivo. El complemento de control de código fuente abre su propia ventana, en el formato que elija, para mostrar las diferencias entre el archivo del usuario en el disco y la versión más reciente del archivo bajo control de código fuente.

 Como alternativa, es posible que el IDE simplemente necesite determinar si un archivo ha cambiado. Por ejemplo, es posible que el IDE necesite determinar si es seguro desproteger un archivo sin informar al usuario. En ese caso, el IDE pasa la `SCC_DIFF_CONTENTS` marca. El complemento de control de código fuente debe comprobar el archivo en disco, byte por byte, en el archivo controlado por código fuente y devolver un valor que indique si los dos archivos son diferentes sin mostrar nada al usuario.

 Como optimización del rendimiento, el complemento de control de código fuente puede usar una alternativa basada en una suma de comprobación o una marca de tiempo en lugar de la comparación byte a byte llamada por `SCC_DIFF_CONTENTS` : estas formas de comparación son obviamente más rápidas pero menos confiables. No todos los sistemas de control de código fuente pueden admitir estos métodos de comparación alternativos y el complemento puede tener que revertir a una comparación de contenido. Todos los complementos de control de código fuente deben admitir, como mínimo, una comparación de contenido.

> [!NOTE]
> Las marcas de diferencia rápida son mutuamente excluyentes. Es válido no pasar marcas, pero no es válido pasar simultáneamente más de una. `SCC_DIFF_QUICK_DIFF`, que es una máscara que combina todas las marcas, se puede usar para realizar pruebas, pero nunca debe pasarse como un parámetro.

|`fOption`|Significado|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Comparación sin distinción entre mayúsculas y minúsculas (se puede usar para una diferencia rápida o visual).|
|SCC_DIFF_IGNORESPACE|Omite el espacio en blanco (se puede usar para una diferencia rápida o visual).|
|SCC_DIFF_QD_CONTENTS|Compara el archivo en modo silencioso, byte a byte.|
|SCC_DIFF_QD_CHECKSUM|Compara el archivo de forma silenciosa a través de una suma de comprobación cuando se admite. Si no se admite, recurre a una comparación de contenido.|
|SCC_DIFF_QD_TIME|Compara el archivo de forma silenciosa a través de su marca de tiempo cuando se admite. Si no se admite, recurre a una comparación de contenido.|

## <a name="see-also"></a>Vea también
- [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
