---
title: "IApplicationDebuggerUI (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IApplicationDebuggerUI (interfaz)"
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI (Interfaz)
Implementado por el entorno de desarrollo integrado \(IDE\) de depurador \(además de `IApplicationDebugger`\) para dar a componente externo más control sobre la interfaz de usuario \(UI\) del depurador.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IApplicationDebuggerUI` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Trae la ventana que contiene el documento especificado de depuración a la parte superior de la interfaz de usuario del depurador.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Trae la ventana que contiene el contexto determinado del documento en la parte superior de la interfaz de usuario del depurador y desplaza la ventana al contexto.|