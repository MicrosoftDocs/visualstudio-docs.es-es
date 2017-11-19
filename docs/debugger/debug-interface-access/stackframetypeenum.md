---
title: StackFrameTypeEnum | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37d8e960d256b8746781668068978aa72f45155c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
 Puntero de marco que se omite; Información de FPO está disponible.  
  
 `FrameTypeTrap`  
 Marco de captura de kernel.  
  
 `FrameTypeTSS`  
 Marco de captura de kernel.  
  
 `FrameTypeStandard`  
 Marco de pila EBP estándar.  
  
 `FrameTypeFrameData`  
 Puntero de marco que se omite; Información de datos de marco está disponible.  
  
 `FrameTypeUnknown`  
 Marco que no tiene ninguna información de depuración.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración son devueltos por una llamada a la [idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)