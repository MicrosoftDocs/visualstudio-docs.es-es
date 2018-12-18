---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d05f49f8fa91a0b193be10169a4dcebcd561f92d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910581"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Muestra el cuadro de diálogo especificado que permite al usuario seleccionar un puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hwndParentDialog`  
 [in] Identificador para el cuadro de diálogo principal.  
  
 `pbstrPortId`  
 [out] Cadena de identificador de puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Un valor devuelto de `S_FALSE` (o un valor devuelto de `S_OK` con el `BSTR` establecido en `NULL`) indica que el usuario hizo clic **cancelar**.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)