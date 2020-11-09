---
title: SetThreadCount | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa SetThreadCount para establecer el recuento global de subprocesos y asignar ese recuento al subproceso actual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01bfdae1dcd11d7df042948308c424b7773b3bb0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048324"
---
# <a name="setthreadcount"></a>SetThreadCount

Establece el recuento de subprocesos globales y asigna ese recuento al subproceso actual.

## <a name="syntax"></a>Sintaxis

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parámetros

[in] `threadCount`

 El número de subprocesos que se va a usar.

## <a name="return-value"></a>Valor devuelto

 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el recuento de subprocesos se ha actualizado.

## <a name="requirements"></a>Requisitos

 **Encabezado:** *FileTracker.h*