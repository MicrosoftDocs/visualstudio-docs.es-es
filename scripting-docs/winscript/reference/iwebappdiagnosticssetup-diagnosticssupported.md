---
title: Iwebappdiagnosticssetup (::D iagnosticsSupported | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984583"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Determina si los diagnósticos se admiten en esta aplicación. Si se ha llamado a [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) en el objeto que implementa esta interfaz con un valor distinto de NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) devuelve `true`. En caso contrario, devuelve `false` y las llamadas a [iwebappdiagnosticssetup (:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) generan un error.  
  
> [!IMPORTANT]
> La [interfaz iwebappdiagnosticssetup (](../../winscript/reference/iwebappdiagnosticssetup-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 Si se ha llamado a [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) en el objeto que implementa esta interfaz con un valor distinto de NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) devuelve `true`. Si no es así, devuelve `false`y las llamadas a [iwebappdiagnosticssetup (:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) generan un error.