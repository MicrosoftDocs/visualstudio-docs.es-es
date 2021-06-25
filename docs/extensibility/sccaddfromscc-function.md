---
description: Esta función permite al usuario buscar archivos que ya están en el sistema de control de código fuente y, posteriormente, hacer que esos archivos forme parte del proyecto actual.
title: Función SccAddFromScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48560f135d73c4e53ba132845f4c768cdf4ac982
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904882"
---
# <a name="sccaddfromscc-function"></a>Función SccAddFromScc
Esta función permite al usuario buscar archivos que ya están en el sistema de control de código fuente y, posteriormente, hacer que esos archivos forme parte del proyecto actual. Por ejemplo, esta función puede obtener un archivo de encabezado común en el proyecto actual sin copiar el archivo. La matriz de archivos devuelta, , contiene la lista de archivos que el usuario `lplpFileNames` quiere agregar al proyecto ide.

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

[in] Estructura de contexto del complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 lpnFiles

[in, out] Búfer para el número de archivos que se van a agregar. (Esto es si se va a liberar la memoria a la `NULL` `lplpFileNames` que apunta. Vea Comentarios para obtener más información).

 lplpFileNames

[in, out] Matriz de punteros a todos los nombres de archivo sin rutas de acceso de directorio. El complemento de control de código fuente asigna y libera esta matriz. Si = 1 y no es , el nombre de la matriz a la que apunta `lpnFiles` contiene la carpeta de `lplpFileNames` `NULL` `lplpFileNames` destino.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Los archivos se localizaron correctamente y se agregaron al proyecto.|
|SCC_I_OPERATIONCANCELED|La operación se canceló sin ningún efecto.|
|SCC_I_RELOADFILE|Es necesario volver a cargar un archivo o proyecto.|

## <a name="remarks"></a>Observaciones
 El IDE llama a esta función. Si el complemento de control de código fuente admite la especificación de una carpeta de destino local, el IDE pasa = 1 y pasa el nombre de la carpeta `lpnFiles` local a `lplpFileNames` .

 Cuando se devuelve la llamada a la función , el complemento ha asignado valores a y , asignando la memoria de la matriz de nombres de archivo según sea `SccAddFromScc` necesario (tenga en cuenta que esta asignación reemplaza el puntero `lpnFiles` `lplpFileNames` en `lplpFileNames` ). El complemento de control de código fuente es responsable de colocar todos los archivos en el directorio del usuario o en la carpeta de designación especificada. A continuación, el IDE agrega los archivos al proyecto ide.

 Por último, el IDE llama a esta función una segunda vez, pasando `NULL` para `lpnFiles` . Esto se interpreta como una señal especial por el complemento de control de código fuente para liberar la memoria asignada para la matriz de nombre de archivo en `lplpFileNames``.`

 `lplpFileNames` es un `char ***` puntero. El complemento de control de código fuente coloca un puntero a una matriz de punteros a nombres de archivo, pasando así la lista de la manera estándar para esta API.

> [!NOTE]
> Las versiones iniciales de la API de VSSCI no proporcionan una manera de indicar el proyecto de destino para los archivos agregados. Para dar cabida a esto, se ha mejorado la semántica del parámetro para que sea un parámetro de entrada y salida en lugar de `lplpFIleNames` un parámetro de salida. Si solo se especifica un archivo, es decir, el valor al que apunta = 1, el primer elemento `lpnFiles` de contiene la carpeta de `lplpFileNames` destino. Para usar esta nueva semántica, el IDE llama a `SccSetOption` la función con el parámetro establecido en `nOption` `SCC_OPT_SHARESUBPROJ` . Si un complemento de control de código fuente no admite la semántica, devuelve `SCC_E_OPTNOTSUPPORTED` . Al hacerlo, se deshabilita el uso de la **característica Agregar desde el control de** código fuente. Si un complemento admite la característica Agregar desde **control de código** fuente ( ), debe admitir la nueva semántica y devolver `SCC_CAP_ADDFROMSCC` `SCC_I_SHARESUBPROJOK` .

## <a name="see-also"></a>Consulta también
- [Funciones de API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
