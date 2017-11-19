---
title: IDebugDocument2::GetName | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocument2::GetName
helpviewer_keywords: IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 717a1eb794e3712427d6b905851c32796c3865c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Obtiene el nombre del documento en una de varias formas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `gnType`  
 [in] Un valor de la [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) enumeración que determina el tipo de nombre para devolver.  
  
 `pbstrFileName`  
 [out] Devuelve una cadena que contiene el nombre del documento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método puede, por ejemplo, devolver el nombre del documento como un título o como un nombre de archivo o incluso parte de un nombre de archivo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)