---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 655911bac1efbafe1838e24e2056282f9036479b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179193"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica el tipo de marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Elementos  
 `FrameTypeFPO`  
 Se omite el puntero de marco. Información de FPO disponible.  
  
 `FrameTypeTrap`  
 Marco de captura de kernel.  
  
 `FrameTypeTSS`  
 Marco de captura de kernel.  
  
 `FrameTypeStandard`  
 Marco de pila EBP estándar.  
  
 `FrameTypeFrameData`  
 Se omite el puntero de marco. Información de datos de marco disponible.  
  
 `FrameTypeUnknown`  
 Marco que no tiene ninguna información de depuración.  
  
## <a name="remarks"></a>Observaciones  
 Los valores de esta enumeración son devueltos por una llamada al método [IDiaStackFrame:: GET_TYPE](../../debugger/debug-interface-access/idiastackframe-get-type.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
