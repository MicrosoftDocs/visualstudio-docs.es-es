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
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 150c8794fb35ca017be7e0873dc0d1b84ebfc38c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
  
  