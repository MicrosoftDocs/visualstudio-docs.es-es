---
title: IDiaFrameData::get_type | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 95232ab69d6f30435807764e1177d15d6e4622d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161428"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera el tipo de marco específico del compilador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 enuncia Devuelve un valor de la enumeración de [enumeración stackframetypeenum (](../../debugger/debug-interface-access/stackframetypeenum.md) que indica el tipo de marco específico del compilador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Enumeración StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)
