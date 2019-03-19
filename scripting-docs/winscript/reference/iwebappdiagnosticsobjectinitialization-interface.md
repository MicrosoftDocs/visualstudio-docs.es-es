---
title: IWebAppDiagnosticsObjectInitialization (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67cf59965d47b2a0e29bbe6280d69acf0000a20d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149580"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>IWebAppDiagnosticsObjectInitialization (Interfaz)
Esta interfaz se puede implementar en clases que implementan [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [IWebAppDiagnosticsSetup (interfaz)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) es implementada por el objeto que implementa [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md). En la mayoría de los casos este objeto es el PDM.  
  
 Una vez creado el objeto, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) se llama con una referencia a la aplicación de depuración PDM y `hPassToObject` parámetro de `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 Esta interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Inicializa el objeto.|