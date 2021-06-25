---
title: Utilidad CreatePkgDef | Microsoft Docs
description: Obtenga información sobre la utilidad CreatePkgDef que toma un archivo .dll para una extensión de Visual Studio como parámetro y crea un archivo .pkgdef para acompaña al archivo .dll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bfbd4b42d9ceddd40e08c28926a59aecba719fe9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898128"
---
# <a name="createpkgdef-utility"></a>Utilidad CreatePkgDef
Toma un .dll para una extensión Visual Studio como parámetro y crea un archivo *.pkgdef* para acompaña al *.dll* archivo. El *archivo .pkgdef* contiene toda la información que, de lo contrario, se escribiría en el registro del sistema cuando se instala la extensión.

> [!NOTE]
> La mayoría de las plantillas de proyecto que se incluyen en Visual Studio SDK crean automáticamente archivos *.pkgdef* como parte del proceso de compilación. Este documento está destinado a aquellos que desean crear paquetes manualmente o convertir paquetes existentes para usar *la implementación de .pkgdef.*

## <a name="syntax"></a>Sintaxis

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumentos
**/out= &lt; FileName&gt;**\
Necesario. Establece el nombre del archivo *de salida .pkgdef* en &lt; &gt; FileName.

**/codebase**\
Opcional. Fuerza el registro con la **utilidad CodeBase.**

**/assembly**\
Fuerza el registro con la **utilidad Assembly.**

**&lt;AssemblyPath&gt;**\
Ruta de acceso del *.dll* desde el que desea generar *el archivo .pkgdef*.

## <a name="remarks"></a>Observaciones
La implementación de extensiones mediante *archivos .pkgdef* reemplaza los requisitos del Registro de versiones anteriores de Visual Studio.

::: moniker range=">=vs-2019"

Los *archivos .pkgdef* deben instalarse en una de las siguientes ubicaciones:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Si la carpeta de instalación es *%localappdata%\Microsoft\Visual Studio\16.0\Extensions \\*, la extensión se reconoce mediante Visual Studio pero está deshabilitada de forma predeterminada. El usuario puede habilitar la extensión mediante **Administrar extensiones**.

Si la carpeta de instalación *es %vsinstalldir%\Common7\IDE\Extensions, \\* la extensión está habilitada de forma predeterminada.

> [!NOTE]
> La **herramienta Administrar extensiones** no se puede usar para acceder a una extensión a menos que se instale como parte de un paquete VSIX.

::: moniker-end

::: moniker range="vs-2017"

Los *archivos .pkgdef* deben instalarse en una de las siguientes ubicaciones:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Si la carpeta de instalación es *%localappdata%\Microsoft\Visual Studio\15.0\Extensions \\*, la extensión se reconoce mediante Visual Studio pero está deshabilitada de forma predeterminada. El usuario puede habilitar la extensión mediante **Extensiones y actualizaciones**.

Si la carpeta de instalación *es %vsinstalldir%\Common7\IDE\Extensions, \\* la extensión está habilitada de forma predeterminada.

> [!NOTE]
> La **herramienta Extensiones y actualizaciones** no se puede usar para acceder a una extensión a menos que se instale como parte de un paquete VSIX.

::: moniker-end

## <a name="see-also"></a>Consulta también
- [Utilidad CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
