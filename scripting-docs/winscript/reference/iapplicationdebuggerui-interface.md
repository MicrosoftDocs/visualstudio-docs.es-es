---
title: IApplicationDebuggerUI (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI (Interfaz)
Implementado por el entorno de desarrollo integrado (IDE) de depurador (además `IApplicationDebugger`) para proporcionar más control sobre la interfaz de usuario (UI) del depurador a un componente externo.  
  
 Además de los métodos heredados de `IUnknown`, el `IApplicationDebuggerUI` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Abre la ventana que contiene el documento de depuración especificado a la parte superior en el depurador de interfaz de usuario.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Abre la ventana que contiene el contexto del documento especificado a la parte superior de la interfaz de usuario del depurador y se desplaza la ventana para el contexto.|