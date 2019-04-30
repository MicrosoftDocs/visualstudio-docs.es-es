---
title: IWefDebuggingSupport interface
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a71adf5371275fbbdc19cdf09be96ef900ec073d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583768"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport interface
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

|Name|Descripción|
|----------|-----------------|
|[GetAutoInsertExtensions (método)](../vsto/getautoinsertextensions-method.md)|Obtiene información acerca de las aplicaciones de Office que se insertarán automáticamente durante la depuración.|
|[SetWefProcessId (método)](../vsto/setwefprocessid-method.md)|Proporciona el identificador de proceso que se ejecutará el contenido del marco de trabajo de extensiones de Web (WEF).|
