---
title: Interfaz Iwefdebuggingsupport (
description: Obtenga información sobre cómo puede usar un entorno de depuración como Visual Studio para facilitar la depuración de aplicaciones Microsoft Office.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6a818973bdc2f62194d6ed0026c0798806fe5f2a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525320"
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
