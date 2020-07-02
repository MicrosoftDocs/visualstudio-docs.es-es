---
title: Interfaz Iwefdebuggingsupport (
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a4883d36c1833c66a2539380184521b070f5c2a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544734"
---
# <a name="iwefdebuggingsupport-interface"></a>Interfaz Iwefdebuggingsupport (
  Implementado por un entorno de depuración, como Visual Studio, para facilitar la depuración de aplicaciones para Office. La aplicación de Office, como Word o Excel, obtiene esta interfaz de Visual Studio y, a continuación, llama a los métodos en la interfaz en determinados puntos durante la sesión de depuración.

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
 En la tabla siguiente se enumeran los métodos que define la interfaz Iwefdebuggingsupport (.

|Nombre|Descripción|
|----------|-----------------|
|[Método Getautoinsertextensions (](../vsto/getautoinsertextensions-method.md)|Obtiene información sobre las aplicaciones de Office que se insertarán automáticamente durante la depuración.|
|[Método Setwefprocessid (](../vsto/setwefprocessid-method.md)|Proporciona el identificador de proceso que ejecutará el contenido del marco de extensiones web (WEF).|
