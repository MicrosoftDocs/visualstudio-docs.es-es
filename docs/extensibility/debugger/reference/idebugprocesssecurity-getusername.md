---
title: IDebugProcessSecurity::GetUserName | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: aa8da8828dbbc314ce976572d1f6bd9d5abf5721
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Obtiene el nombre de usuario desde el proveedor del puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrUserName`  
 [out] Una cadena que contiene el nombre de usuario.  
  
## <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve `S_OK`. En caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 `GetUserName`Devuelve el nombre de usuario que se muestra en el **nombre de usuario** columna de la **adjuntar al proceso** cuadro de diálogo. Para ver el **adjuntar al proceso** cuadro de diálogo, haga clic en **adjuntar al proceso** en el **herramientas** menú en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)