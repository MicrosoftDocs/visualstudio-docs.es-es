---
title: MarK | Microsoft Docs
description: Obtenga información sobre cómo la opción Mark de VSPerfCmd.exe inserta los detalles especificados en el archivo de datos de generación de perfiles.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 33a343be010a5bf9cc0d9ba3e4251d92fd720656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917810"
---
# <a name="mark"></a>Marca
La opción **Mark** de *VSPerfCmd.exe* inserta la información especificada en el archivo de datos de generación de perfiles. La marca puede incluirse en un informe de VSPerfReport independiente o en la vista de informe de marca de la interfaz de usuario del generador de perfiles. **Mark** se puede usar para especificar los puntos inicial y final en los filtros de informe y vista.

 La opción **Mark** debe ser la única especificada en la línea de comandos.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parámetros
 `MarkID` Entero definido por el usuario que aparece como el identificador de marca en los informes y vistas del generador de perfiles. `MarkID` no tiene que ser único.

 `MarkName` (Opcional) Cadena definida por el usuario que aparece como el nombre de la marca en los informes y vistas del generador de perfiles. Si `MarkName` no se especifica, el campo de nombre de la marca aparecerá vacío. Entrecomille las cadenas que contengan espacios o barras diagonales ("/").

## <a name="example"></a>Ejemplo
 En este ejemplo se inserta una marca con un identificador "123" y el nombre de marca "TestMark".

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
