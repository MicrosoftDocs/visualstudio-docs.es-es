---
title: SCRIPTPROP_HOSTKEEPALIVE (propiedad) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734145"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE (Propiedad)
Se utiliza para especificar si se permite o no el motor de scripting se debe mantener totalmente funcional si hay referencias pendientes.  
  
 Use [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) para establecer esta propiedad en `true`. Si esta propiedad se establece en `true`, se mantiene el motor de scripting totalmente funcional mientras hay al menos una referencia pendiente en el propio motor de secuencias de comandos o en un `IDispatch` puntero a un objeto de JavaScript que se crean mediante el formato de script motor de búsqueda. Cuando esta propiedad se establece en `true`, debe cerrar explícitamente no o restablecer el motor de scripts mediante el [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) o [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) métodos. La versión de la última referencia a un objeto de secuencia de comandos cierra el motor de scripts.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Requisitos  
 Esta propiedad sólo aparece en la versión de activscp.idl que se instala con [!INCLUDE[win8](../../javascript/includes/win8-md.md)], con 2707082 KB para Internet Explorer 8 en [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], o con 2722913 KB para Internet Explorer 9 en [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] o [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].