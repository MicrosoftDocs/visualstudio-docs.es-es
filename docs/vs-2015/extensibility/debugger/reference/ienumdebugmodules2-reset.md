---
title: IEnumDebugModules2::Reset | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugModules2::Reset
helpviewer_keywords:
- IEnumDebugModules2::Reset
ms.assetid: f6ff364c-2644-4919-b950-3cb82eb6f601
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c694981166e7645d1d697a2c9752330cd0f7000d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950152"
---
# <a name="ienumdebugmodules2reset"></a>IEnumDebugModules2::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restablece la enumeración al primer elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Después de llamar a este método, la siguiente llamada a la [siguiente](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) método devuelve el primer elemento de la enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

