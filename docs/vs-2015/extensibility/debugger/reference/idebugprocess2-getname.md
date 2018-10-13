---
title: IDebugProcess2::GetName | Microsoft Docs
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
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 557a6f32a6d9b353db1567887e0308e7ba8cac2e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274097"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el título, el nombre descriptivo o el nombre de archivo del proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetName(   
   GETNAME_TYPE  gnType,  
   BSTR*         pbstrName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `gnType`  
 [in] Un valor de la [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) enumeración que especifica qué tipo de nombre para devolver.  
  
 `pbstrName`  
 [out] Devuelve el nombre del proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)

