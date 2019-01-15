---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be9a07c961e62870319de10cad77eaee8e12ef1c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864016"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Especifica el tipo de marco de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
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
 Puntero de marco que se omite; Información de FPO disponible.  
  
 `FrameTypeTrap`  
 Marco de captura del kernel.  
  
 `FrameTypeTSS`  
 Marco de captura del kernel.  
  
 `FrameTypeStandard`  
 Marco de pila EBP estándar.  
  
 `FrameTypeFrameData`  
 Puntero de marco que se omite; Información de datos del marco disponible.  
  
 `FrameTypeUnknown`  
 Marco que no tiene ninguna información de depuración.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se devuelven mediante una llamada a la [Idiastackframe](../../debugger/debug-interface-access/idiastackframe-get-type.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)