---
title: IDebugField::Equal | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::Equal
helpviewer_keywords: IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30ef8524fbc5d6451bcc302079f769fd05c66185
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Este método compara este campo con el campo especificado para la igualdad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pField`  
 [in] El campo para comparar a este.  
  
## <a name="return-value"></a>Valor devuelto  
 Si los campos son iguales, devuelve `S_OK`. Si los campos son diferentes, devuelve `S_FALSE.` en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)