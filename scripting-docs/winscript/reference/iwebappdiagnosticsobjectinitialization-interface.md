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
ms.openlocfilehash: a992f8512d4927eeb58d6437ccb830abda688b28
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443686"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>IWebAppDiagnosticsObjectInitialization (Interfaz)
Esta interfaz se puede implementar en clases que implementan [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [IWebAppDiagnosticsSetup (interfaz)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) es implementada por el objeto que implementa [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md). En la mayoría de los casos este objeto es el PDM.  
  
 Una vez creado el objeto, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) se llama con una referencia a la aplicación de depuración PDM y `hPassToObject` parámetro de `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsObjectInitialization` se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 Esta interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Inicializa el objeto.|