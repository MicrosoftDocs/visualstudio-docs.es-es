---
title: SccAddFromScc (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 199f89d7c2ce4c9674ed9d79ec13a1b392b70371
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707008"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc (función)
Esta función permite al usuario examinar los archivos que ya están en el sistema de control de código fuente y posteriormente realizar esas partes de los archivos del proyecto actual. Por ejemplo, esta función puede obtener un archivo de encabezado común en el proyecto actual sin copiar el archivo. La matriz de devolución de los archivos, `lplpFileNames`, contiene la lista de archivos que el usuario desea agregar al proyecto IDE.

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

[in] La estructura de contexto de complemento de control de origen.

 hWnd

[in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.

 lpnFiles

[in, out] Un búfer para el número de archivos que se agregan. (Esto es `NULL` si la memoria indicada por `lplpFileNames` consiste en liberarse. Vea la sección Comentarios para obtener más información).

 lplpFileNames

[in, out] Una matriz de punteros a todos los nombres de archivo sin las rutas de acceso de directorio. Esta matriz se asigna y libera el complemento de control de código fuente. Si `lpnFiles` = 1 y `lplpFileNames` no `NULL`, el nombre de la matriz señalada por `lplpFileNames` contiene la carpeta de destino.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Los archivos correctamente se encuentra y se agrega al proyecto.|
|SCC_I_OPERATIONCANCELED|Se canceló la operación no tiene ningún efecto.|
|SCC_I_RELOADFILE|Debe volver a cargar un archivo o proyecto.|

## <a name="remarks"></a>Comentarios
 El IDE llama a esta función. Si el complemento de control de código fuente admite la especificación de una carpeta de destino local, pasa el IDE `lpnFiles` = 1 y pasa el nombre de la carpeta local en `lplpFileNames`.

 Cuando la llamada a la `SccAddFromScc` devuelve la función, el complemento se les asignan valores a `lpnFiles` y `lplpFileNames`, asignar la memoria para la matriz de nombre de archivo según sea necesario (tenga en cuenta que esta asignación reemplaza el puntero en `lplpFileNames`). El complemento de control de código fuente es responsable de colocar todos los archivos en el directorio del usuario o en la carpeta designación especificado. El IDE, a continuación, agrega los archivos al proyecto IDE.

 Por último, el IDE llama a esta función una segunda vez, pasando `NULL` para `lpnFiles`. Esto se interpreta como una señal especial mediante el complemento para liberar la memoria asignada para la matriz de nombres de archivo de control de código fuente `lplpFileNames``.`

 `lplpFileNames` es un `char ***` puntero. El complemento de control de código fuente coloca un puntero a una matriz de punteros a los nombres de archivo, por tanto, pasar la lista de la manera estándar para esta API.

> [!NOTE]
>  Las versiones iniciales de la API VSSCI no proporcionó una manera de indicar el proyecto de destino para los archivos agregados. Para dar cabida a esto, la semántica de la `lplpFIleNames` parámetro se han mejorado para que sea un parámetro de entrada/salida, en lugar de un parámetro de salida. Si solo se especifica un único archivo, es decir, el valor señalado por `lpnFiles` = 1, entonces el primer elemento de `lplpFileNames` contiene la carpeta de destino. Para usar esta nueva semántica, las llamadas IDE el `SccSetOption` funcionando con el `nOption`parámetro establecido en `SCC_OPT_SHARESUBPROJ`. Si un complemento de control de origen no es compatible con la semántica, devuelve `SCC_E_OPTNOTSUPPORTED`. Realizar por lo que deshabilita el uso de la **agregar Control de código fuente** característica. Si un complemento admite el **agregar Control de código fuente** característica (`SCC_CAP_ADDFROMSCC`), a continuación, debe admitir la nueva semántica y devolver `SCC_I_SHARESUBPROJOK`.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)