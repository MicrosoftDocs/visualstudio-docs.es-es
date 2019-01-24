---
title: IWefDebuggingSupport (interfaz)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 73aff964cfb66d33e308aef6448fc0f0b1b27c09
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901024"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport (interfaz)
  Implementa un entorno de depuración, como Visual Studio, para facilitar la depuración de aplicaciones para Office. La aplicación de Office, como Word o Excel, obtiene esta interfaz desde Visual Studio y, a continuación, llama a métodos en la interfaz en ciertos puntos durante la sesión de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp 
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se enumera los métodos que define la interfaz IWefDebuggingSupport.  
  
|nombre|Descripción|  
|----------|-----------------|  
|[GetAutoInsertExtensions (método)](../vsto/getautoinsertextensions-method.md)|Obtiene información acerca de las aplicaciones de Office que se insertarán automáticamente durante la depuración.|  
|[SetWefProcessId (método)](../vsto/setwefprocessid-method.md)|Proporciona el identificador de proceso que se ejecutará el contenido del marco de trabajo de extensiones de Web (WEF).|  
