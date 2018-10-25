---
title: Idiaenumsegments | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get__NewEnum method
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5078a08c10f4ff54240d2cf8cf4c8d1740a7fc1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938739"
---
# <a name="idiaenumsegmentsgetnewenum"></a>IDiaEnumSegments::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pRetVal  
 [out] Devuelve el `IUnknown` interfaz que representa el <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versión de este enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)



