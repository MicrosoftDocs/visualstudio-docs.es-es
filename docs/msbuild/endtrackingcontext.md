---
title: EndTrackingContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bf8720efab88556092e6552a8ffa47cb1151fef
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946386"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
Finaliza el contexto de seguimiento actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el contexto de seguimiento ha finalizado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** FileTracker.h  
  
## <a name="see-also"></a>Vea también  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)