---
title: IWefDebuggingSupport (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b132c51e12d553bcd6e722e87c8aeee96be5e5c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
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
  
  