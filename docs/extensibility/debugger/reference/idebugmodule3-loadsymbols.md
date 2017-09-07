---
title: IDebugModule3::LoadSymbols | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: 11
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
ms.openlocfilehash: 00b357a7c122de2788875632b770c4346963d975
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Carga los símbolos del módulo actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve `S_OK`. Si se produce un error, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método carga los símbolos desde la ruta de acceso de búsqueda actual (que puede modificarse mediante una llamada a la [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) método).  
  
 Este método es preferible el [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
