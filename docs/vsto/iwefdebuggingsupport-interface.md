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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9fc319429414c8976d748a30ecdd1e164ce22b63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962267"
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
