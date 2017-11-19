---
title: IDebugDocument2::GetDocumentClassID | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocument2::GetDocumentClassID
helpviewer_keywords: IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e216cf5af1ad22acf81f46ca385f7092e8ee8316
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Obtiene el identificador de clase del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```csharp  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pclsid`  
 [out] Devuelve un GUID que es el identificador de clase del documento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El GUID de clase puede usarse para crear instancias de clases individuales de cada uno de los cuales representa un documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)