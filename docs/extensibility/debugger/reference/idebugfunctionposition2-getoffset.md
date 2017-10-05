---
title: IDebugFunctionPosition2::GetOffset | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugFunctionPosition2::GetOffset
helpviewer_keywords:
- IDebugFunctionPosition2::GetOffset
ms.assetid: 60943782-aec7-4be2-b222-1984ed53a543
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 03bb7bc8cbecff6b74f5ea2c2e0d95f516c8f536
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="idebugfunctionposition2getoffset"></a>IDebugFunctionPosition2::GetOffset
Recupera la posición de la función en el documento de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetOffset(   
   TEXT_POSITION* pPosition  
);  
```  
  
```csharp  
int GetOffset(  
   TEXT_POSITION[] pPosition  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pPosition`  
 [entrada, salida] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que se rellena con la posición de la función en un documento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
