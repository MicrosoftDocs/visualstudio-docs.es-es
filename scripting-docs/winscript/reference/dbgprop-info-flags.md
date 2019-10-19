---
title: DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b8131531292e0f88108942648073883050dd609
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572582"
---
# <a name="dbgprop_info_flags"></a>DBGPROP_INFO_FLAGS
Se usa para especificar `DebugPropertyInfo` campos  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Miembros  
 DBGPROP_INFO_NAME  
 Inicializa el campo de `bstrName`.  
  
 DBGPROP_INFO_TYPE  
 Inicializa el campo de `bstrType`.  
  
 DBGPROP_INFO_VALUE  
 Inicializa el campo de `bstrValue`.  
  
 DBGPROP_INFO_FULLNAME  
 Inicializa el campo de `bstrFullName`.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Inicializa el campo de `dwAttrib`.  
  
 DBGPROP_INFO_DEBUGPROP  
 Inicializa el `pDebugProp` campo que contiene una interfaz de `IDebugProperty`.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Especifica que el campo de valor debe contener el valor de expansión automática, si está disponible, para este tipo de objeto.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [estructura debugpropertyinfo (](../../winscript/reference/debugpropertyinfo-structure.md)  
 [IDebugProperty (Interfaz)](../../winscript/reference/idebugproperty-interface.md)