---
title: SuspendTracking | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b484ce1bd47d01092ff28d60b457012805cb16e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31568629"
---
# <a name="suspendtracking"></a>SuspendTracking
Suspende el seguimiento en el contexto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp 
HRESULT WINAPI SuspendTracking(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el seguimiento se ha suspendido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** FileTracker.h  
  
## <a name="see-also"></a>Vea también  
 [ResumeTracking](../msbuild/resumetracking.md)