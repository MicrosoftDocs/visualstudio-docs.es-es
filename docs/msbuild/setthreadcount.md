---
title: SetThreadCount | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b36da837ae1f4c327969b398c3964bfd6dd2aea3
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302755"
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
 **Encabezado:** FileTracker.h