---
title: IWefDebuggingSupport (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8e8a1bc770ce030902691a8ee4f2634c79cbab9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport (Interfaz)
  Implementa un entorno de depuración, como Visual Studio, para facilitar la depuración de aplicaciones para Office. La aplicación de Office, como Word o Excel, obtiene de esta interfaz desde Visual Studio y, a continuación, llama a métodos en la interfaz en ciertos puntos durante la sesión de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|[GetAutoInsertExtensions (método)](../vsto/getautoinsertextensions-method.md)|Obtiene información sobre las aplicaciones de Office que se van a insertar automáticamente durante la depuración.|  
|[SetWefProcessId (método)](../vsto/setwefprocessid-method.md)|Proporciona el identificador de proceso que se ejecutará el contenido del marco de trabajo de las extensiones de Web (WEF).|  
  
  