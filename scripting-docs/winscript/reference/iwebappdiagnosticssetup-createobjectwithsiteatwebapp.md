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
ms.openlocfilehash: 42f92cfe9245a5e3a6342c31fc996ae2db50ef70
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443700"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Este método crea comparte la clase cuyo identificador se pasa con `rclsid` mediante el `dwClsContext`. Esto es similar a la forma [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) funciona, salvo que en el caso de `CreateObjectWithSiteAtWebApp` el objeto se crea de forma asincrónica en el subproceso de interfaz de usuario de la aplicación web. El objeto especificado por el identificador de clase debe implementar [IWebAppDiagnosticsObjectInitialization (interfaz)](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Una vez creado el objeto, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) se llama con una referencia a la aplicación de depuración PDM y `hPassToObject` parámetro de `CreateObjectWithSiteAtWebApp`. Puede usar este método para pasar a la aplicación un identificador a una canalización anónima que ha copiado mediante [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
> [IWebAppDiagnosticsSetup (interfaz)](../../winscript/reference/iwebappdiagnosticssetup-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
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