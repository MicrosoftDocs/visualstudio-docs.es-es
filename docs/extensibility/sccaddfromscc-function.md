---
title: Función SccAddFromScc (SccAddFromScc) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701247"
---
# <a name="sccaddfromscc-function"></a>Función SccAddFromScc
Esta función permite al usuario buscar archivos que ya están en el sistema de control de código fuente y, posteriormente, hacer que esos archivos formen parte del proyecto actual. Por ejemplo, esta función puede obtener un archivo de encabezado común en el proyecto actual sin copiar el archivo. La matriz return `lplpFileNames`de archivos, , contiene la lista de archivos que el usuario desea agregar al proyecto IDE.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>Parámetros
 pvContext

[en] La estructura de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpnFiles

[adentro, fuera] Un búfer para el número de archivos que se van a agregar. (Esto `NULL` es si se `lplpFileNames` va a liberar la memoria señalada por. Consulte Comentarios para obtener más información.)

 lplpFileNames

[adentro, fuera] Matriz de punteros a todos los nombres de archivo sin rutas de directorio. Esta matriz se asigna y libera mediante el complemento de control de código fuente. Si `lpnFiles` es `lplpFileNames` 1 `NULL`y no es , el `lplpFileNames` primer nombre de la matriz a la que apunta contiene la carpeta de destino.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Los archivos se han localizado correctamente y se agregaron al proyecto.|
|SCC_I_OPERATIONCANCELED|La operación fue cancelada sin efecto.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta función. Si el complemento de control de código fuente admite la `lpnFiles` especificación de una carpeta de `lplpFileNames`destino local, el IDE pasa el número 1 y pasa el nombre de la carpeta local a .

 Cuando se devuelve `SccAddFromScc` la llamada a la función, el complemento ha asignado valores a `lpnFiles` y `lplpFileNames`, asignando la `lplpFileNames`memoria para la matriz de nombres de archivo según sea necesario (tenga en cuenta que esta asignación reemplaza el puntero en ). El complemento de control de código fuente es responsable de colocar todos los archivos en el directorio del usuario o en la carpeta de designación especificada. A continuación, el IDE agrega los archivos al proyecto IDE.

 Por último, el IDE llama a `NULL` esta `lpnFiles`función una segunda vez, pasando por . Esto se interpreta como una señal especial por el plug-in de control de código fuente para liberar la memoria asignada para la matriz de nombres de archivo en`lplpFileNames``.`

 `lplpFileNames`es `char ***` un puntero. El complemento de control de código fuente coloca un puntero a una matriz de punteros a nombres de archivo, pasando así la lista de la manera estándar para esta API.

> [!NOTE]
> Las versiones iniciales de la API de VSSCI no proporcionaban una manera de indicar el proyecto de destino para los archivos agregados. Para dar cabida a `lplpFIleNames` esto, se ha mejorado la semántica del parámetro para convertirlo en un parámetro de entrada/salida en lugar de un parámetro de salida. Si sólo se especifica un único archivo, es `lpnFiles` decir, el valor al `lplpFileNames` que se señala el valor 1, a continuación, el primer elemento de contiene la carpeta de destino. Para usar estas nuevas semánticas, `SccSetOption` el `nOption`IDE `SCC_OPT_SHARESUBPROJ`llama a la función con el parámetro establecido en . Si un complemento de control de código fuente `SCC_E_OPTNOTSUPPORTED`no admite la semántica, devuelve . Al hacerlo, se deshabilita el uso de la característica Agregar desde El control de **código fuente.** Si un complemento admite la característica **Agregar desde Control** de código fuente (`SCC_CAP_ADDFROMSCC`), debe admitir la nueva semántica y devolver `SCC_I_SHARESUBPROJOK`.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
