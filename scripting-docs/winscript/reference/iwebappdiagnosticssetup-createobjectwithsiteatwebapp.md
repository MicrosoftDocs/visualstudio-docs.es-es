---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26403a168268e817644637544d64d4205c398b75
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157664"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Este método crea comparte la clase cuyo identificador se pasa con `rclsid` mediante el `dwClsContext`. Esto es similar a la forma [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) funciona, salvo que en el caso de `CreateObjectWithSiteAtWebApp` el objeto se crea de forma asincrónica en el subproceso de interfaz de usuario de la aplicación web. El objeto especificado por el identificador de clase debe implementar [IWebAppDiagnosticsObjectInitialization (interfaz)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Una vez creado el objeto, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) se llama con una referencia a la aplicación de depuración PDM y `hPassToObject` parámetro de `CreateObjectWithSiteAtWebApp`. Puede usar este método para pasar a la aplicación un identificador a una canalización anónima que ha copiado mediante [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [IWebAppDiagnosticsSetup (interfaz)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rclsid`  
 El identificador de clase de la clase para crear.  
  
 `dwClsContext`  
 El contexto en que se ejecutará el código. En la mayoría de los casos es CLSCTX_INPROC_SERVER.  
  
 `riid`  
 No se utiliza.  
  
 `hPassToObject`  
 Un valor que se pasará al objeto una vez que se crea en el subproceso de interfaz de usuario, si el objeto implementa [IWebAppDiagnosticsObjectInitialization (interfaz)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).