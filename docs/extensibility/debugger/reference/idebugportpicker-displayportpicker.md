---
title: IDebugPortPicker::DisplayPortPicker | Documentos de Microsoft
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
ms.openlocfilehash: bb43ac1bdf173de8e7224f154ecb57cca53abd8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. Un valor devuelto de `S_FALSE` (o un valor devuelto de `S_OK` con el `BSTR` establecido en `NULL`) indica que el usuario hizo clic **cancelar**.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)