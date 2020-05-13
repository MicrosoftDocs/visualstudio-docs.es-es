---
title: Función SccDiff (SccDiff) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b68df68ce7fa4ad5cbc98db256204ddf8623d2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701022"
---
# <a name="sccdiff-function"></a>Función SccDiff
Esta función muestra (o, opcionalmente, solo comprueba) las diferencias entre el archivo actual (en el disco local) y su última versión protegida en el sistema de control de código fuente.

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

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpFileName

[en] Nombre de archivo para el que se solicita la diferencia.

 fOptions

[en] Banderas de mando. Para obtener información detallada, vea la sección Comentarios de.

 pvOptions

[en] Opciones específicas del complemento de control de código fuente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La copia de trabajo y la versión del servidor son idénticas.|
|SCC_I_FILESDIFFERS|La copia de trabajo difiere de la versión bajo control de código fuente.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|
|SCC_E_FILENOTCONTROLLED|El archivo no está bajo control de código fuente.|
|SCC_E_NOTAUTHORIZED|El usuario no puede realizar esta operación.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención. Se recomienda un reintento.|
|SCC_E_NONSPECIFICERROR|Error inespecífico; no se obtuvo la diferencia de archivo.|
|SCC_E_FILENOTEXIST|No se encontró el archivo local.|

## <a name="remarks"></a>Observaciones
 Esta función sirve para dos propósitos diferentes. De forma predeterminada, muestra una lista de cambios en un archivo. El complemento de control de código fuente abre su propia ventana, en el formato que elija, para mostrar las diferencias entre el archivo del usuario en el disco y la última versión del archivo bajo control de código fuente.

 Como alternativa, el IDE puede simplemente necesitar determinar si un archivo ha cambiado. Por ejemplo, el IDE puede necesitar determinar si es seguro desproteger un archivo sin informar al usuario. En ese caso, el IDE `SCC_DIFF_CONTENTS` pasa en la bandera. El complemento de control de código fuente debe comprobar el archivo en el disco, byte a byte, con el archivo controlado por código fuente y devolver un valor que indica si los dos archivos son diferentes sin mostrar nada al usuario.

 Como optimización del rendimiento, el complemento de control de código fuente puede utilizar una alternativa basada en `SCC_DIFF_CONTENTS`una suma de comprobación o una marca de tiempo en lugar de la comparación byte a byte que pide: estas formas de comparación son obviamente más rápidas pero menos confiables. No todos los sistemas de control de código fuente pueden admitir estos métodos de comparación alternativos, y el complemento puede tener que recurrir a una comparación de contenido. Todos los complementos de control de código fuente deben admitir, como mínimo, una comparación de contenido.

> [!NOTE]
> Las banderas de diferencia rápida son mutuamente excluyentes. Es válido pasar ninguna marca, pero no es válido pasar simultáneamente más de uno. `SCC_DIFF_QUICK_DIFF`, que es una máscara que combina todas las marcas, se puede utilizar para probar, pero nunca se debe pasar como parámetro.

|`fOption`|Significado|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Comparación sin distinción entre mayúsculas y minúsculas (se puede utilizar para diferencias visuales o rápidas).|
|SCC_DIFF_IGNORESPACE|Ignora el espacio en blanco (se puede utilizar para la diferencia rápida o visual).|
|SCC_DIFF_QD_CONTENTS|Compara silenciosamente el archivo, byte a byte.|
|SCC_DIFF_QD_CHECKSUM|Compara el archivo de forma silenciosa a través de una suma de comprobación cuando se admite. Si no se admite, vuelve a una comparación de contenido.|
|SCC_DIFF_QD_TIME|Compara silenciosamente el archivo a través de su marca de tiempo cuando se admite. Si no se admite, vuelve a una comparación de contenido.|

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
