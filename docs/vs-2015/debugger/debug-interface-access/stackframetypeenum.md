---
title: StackFrameTypeEnum | Microsoft Docs
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
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de80fd054459556e273427b666175751ced203fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740369"
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



