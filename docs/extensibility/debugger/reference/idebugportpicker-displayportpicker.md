---
title: "IDebugPortPicker::DisplayPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DisplayPortPicker"
  - "IDebugPortPicker::DisplayPortPicker"
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Muestra el cuadro de diálogo especificado que permite al usuario seleccionar un puerto.  
  
## Sintaxis  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```c#  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### Parámetros  
 `hwndParentDialog`  
 \[in\]  Identificador del cuadro de diálogo primario.  
  
 `pbstrPortId`  
 \[out\]  Cadena de identificador de puerto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Un valor devuelto de `S_FALSE` \(o un valor devuelto de `S_OK` con `BSTR` establecido en `NULL`\) indica que el usuario hizo clic en **Cancelar**.  
  
## Vea también  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)