---
title: SCRIPTPROP_HOSTKEEPALIVE (propiedad) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724bfcb1ec42617cda4c89269cb0160accafb1a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840361"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE (Propiedad)
Se utiliza para especificar si el motor de scripting se debe mantener totalmente funcional si hay referencias pendientes.  
  
 Use [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) para establecer esta propiedad en `true`. Si esta propiedad se establece en `true`, se mantiene el motor de scripting totalmente funcional, siempre hay al menos una referencia pendiente para el motor de scripting o a un `IDispatch` puntero a un objeto de JavaScript creado mediante el uso de las secuencias de comandos motor. Cuando esta propiedad se establece en `true`, explícitamente no debe cerrar o restablecer el motor de scripts mediante el [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) o [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) métodos. La versión de la última referencia a un objeto de script cierra el motor de scripts.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Requisitos  
 Esta propiedad solo aparece en la versión de activscp.idl que se instala con [!INCLUDE[win8](../../javascript/includes/win8-md.md)], con 2707082 KB para Internet Explorer 8 en [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], o con 2722913 KB para Internet Explorer 9 en [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] o [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].