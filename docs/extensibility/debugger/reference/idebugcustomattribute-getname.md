---
title: IDebugCustomAttribute::GetName | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetName
helpviewer_keywords: IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8237fe3ad25baa912ee3a1eb84da533d788346cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Obtiene el nombre del atributo personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bstrName`  
 [out] Devuelve una cadena que contiene el nombre del atributo personalizado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El nombre devuelto por este método se corresponde con el nombre de la clase que se utiliza para declarar el atributo. Esto puede no corresponden exactamente en el nombre de la propia clase de atributo personalizado como C# permite el sufijo "Attribute" para que se van a quitar de un nombre de atributo personalizado cuando se utiliza en una declaración.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)