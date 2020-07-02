---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 887e4ce44662cc591fee64f5e0549edcdcbc14af
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835711"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicializa el motor de scripting.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_FAIL` si se produjo un error durante la inicialización.  
  
## <a name="remarks"></a>Comentarios  
 Antes de que se pueda usar el motor de scripting, se debe llamar a uno de los métodos siguientes: `IPersist*::Load` , `IPersist*::InitNew` o `IActiveScriptParse32::InitNew` . La semántica de este método es idéntica a `IPersistStreamInit::InitNew` , en que este método indica al motor de scripting que se inicialice a sí mismo. Tenga en cuenta que no es válido llamar a `IPersist*::InitNew` ni a `IActiveScriptParse32::InitNew` y `IPersist*::Load` , ni a, ni a, ni a `IPersist*::InitNew` `IActiveScriptParse32::InitNew` `IPersist*::Load` una vez más de una vez.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)