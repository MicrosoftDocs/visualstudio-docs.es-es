---
title: StopTrackingAndCleanup | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ffbebd651087d9aa877d0e257947352a0d0275e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154829"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Detiene todo el seguimiento y libera la memoria que ha usado la sesión de seguimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el seguimiento se ha detenido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** *FileTracker.h*  
  
## <a name="see-also"></a>Vea también  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)