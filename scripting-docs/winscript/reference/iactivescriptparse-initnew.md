---
title: 'Iactivescriptparse:: InitNew | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0998bea50d7839f93111aa6b116934fae35bfa3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089991"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inicializa el motor de scripting.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_FAIL` si se produjo un error durante la inicialización.  
  
## <a name="remarks"></a>Comentarios  
 Antes de que se puede usar el motor de scripting, debe llamarse uno de los métodos siguientes: `IPersist*::Load`, `IPersist*::InitNew`, o `IActiveScriptParse::InitNew`. La semántica de este método es idéntica a `IPersistStreamInit::InitNew`, ya que este método indica al motor de scripting que se inicialice. Tenga en cuenta que no es válido llamar a ambos `IPersist*::InitNew` o `IActiveScriptParse::InitNew` y `IPersist*::Load`, ni es válido llamar a `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, o `IPersist*::Load` más de una vez.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)