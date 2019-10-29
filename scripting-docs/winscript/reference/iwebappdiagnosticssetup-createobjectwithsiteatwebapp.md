---
title: 'Iwebappdiagnosticssetup (:: CreateObjectWithSiteAtWebApp | Microsoft Docs'
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
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984607"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Este método crea conjuntamente la clase cuyo identificador se pasa con `rclsid` mediante el `dwClsContext`. Esto es similar a la manera en que [iremotedebugapplication (:: CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) funciona, salvo que en el caso de `CreateObjectWithSiteAtWebApp` el objeto se crea de forma asincrónica en el subproceso de la interfaz de usuario de la aplicación Web. El objeto especificado por el identificador de clase debe implementar la [interfaz iwebappdiagnosticsobjectinitialization (](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Una vez creado el objeto, se llama a [iwebappdiagnosticsobjectinitialization (:: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) con una referencia a la aplicación de depuración de PDM y el parámetro `hPassToObject` de `CreateObjectWithSiteAtWebApp`. Puede usar este método para pasar a la aplicación un identificador a una canalización anónima que haya copiado mediante [DuplicateHandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle).  
  
> [!IMPORTANT]
> La [interfaz iwebappdiagnosticssetup (](../../winscript/reference/iwebappdiagnosticssetup-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rclsid`  
 IDENTIFICADOR de clase de la clase que se va a crear.  
  
 `dwClsContext`  
 Contexto en el que se ejecutará el código. En la mayoría de los casos, es CLSCTX_INPROC_SERVER.  
  
 `riid`  
 No se utiliza.  
  
 `hPassToObject`  
 Un valor que se pasará al objeto una vez que se crea en el subproceso de la interfaz de usuario, si el objeto implementa la [interfaz iwebappdiagnosticsobjectinitialization (](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).