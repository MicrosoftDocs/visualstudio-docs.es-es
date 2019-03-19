---
title: IApplicationDebuggerUI (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f138492e5b0a465bb0f101c15457ed1021ab3d5a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146189"
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI (Interfaz)
Implementado por el entorno de desarrollo integrado (IDE) de depurador (además `IApplicationDebugger`) para proporcionar a un componente externo mayor control sobre la interfaz de usuario (UI) del depurador.  
  
 Además de los métodos heredados de `IUnknown`, el `IApplicationDebuggerUI` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Ofrece interfaz de usuario de la ventana que contiene el documento de depuración especificado en la parte superior en el depurador.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Pone la ventana que contiene el contexto del documento especificado en la parte superior de la interfaz de usuario del depurador y se desplaza a la ventana para el contexto.|