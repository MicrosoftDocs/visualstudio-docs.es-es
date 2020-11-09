---
title: StartTrackingContextWithRoot | Microsoft Docs
description: Aprenda a usar StartTrackingContextWithRoot de MSBuild para iniciar un contexto de seguimiento mediante un archivo de respuesta que especifica un marcador raíz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccca75a0fe525c4e1d9f421b2264070ebda9bdf3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048134"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Inicia un contexto de seguimiento con un archivo de respuesta que especifica un marcador raíz.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parámetros

[in] `intermediateDirectory`

 El directorio en el que almacenar el registro de seguimiento.

[in] `taskName`

 Identifica el contexto de seguimiento. Este nombre se usa para crear el nombre del archivo de registro.

[in] `rootMarkerResponseFile`

 El nombre de ruta de acceso de un archivo de respuesta que contiene un marcador raíz. El nombre de raíz se usa para agrupar todo el seguimiento de un contexto conjuntamente.

## <a name="return-value"></a>Valor devuelto

 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el contexto de seguimiento se ha creado.

## <a name="requirements"></a>Requisitos

 **Encabezado:** *FileTracker.h*

## <a name="see-also"></a>Consulte también

- [StartTrackingContext](../msbuild/starttrackingcontext.md)