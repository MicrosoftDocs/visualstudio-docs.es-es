---
title: IDebugProcessSecurity::GetUserName | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f13d7597877104613f0e6ef6380abf0b6bc2a594
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891477"
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
 `GetUserName` Devuelve el nombre de usuario que se muestra en el **nombre de usuario** columna de la **asociar al proceso** cuadro de diálogo. Para ver el **asociar al proceso** cuadro de diálogo, haga clic en **asociar al proceso** en el **herramientas** menú en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)