---
title: SetThreadCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: SetThreadCount
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 7c25dbb399a3be2af9b181c7ccbf495cc03bec19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="setthreadcount"></a>SetThreadCount
Establece el recuento de subprocesos globales y asigna ese recuento al subproceso actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `threadCount`  
 El número de subprocesos que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el recuento de subprocesos se ha actualizado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** FileTracker.h