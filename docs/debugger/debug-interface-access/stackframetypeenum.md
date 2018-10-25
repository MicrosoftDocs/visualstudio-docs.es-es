---
title: StackFrameTypeEnum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: fcf5e120e769b69c064306432c3026194eb0d851
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853942"
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