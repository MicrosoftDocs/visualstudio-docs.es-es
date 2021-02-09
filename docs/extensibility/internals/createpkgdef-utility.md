---
title: Utilidad CreatePkgDef | Microsoft Docs
description: Obtenga información sobre la utilidad CreatePkgDef que toma un archivo. dll para una extensión de Visual Studio como parámetro y crea un archivo. pkgdef para acompañar el archivo. dll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9822319a74d1374ef2a88d4f9231e6fd86b1e5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884538"
---
# <a name="createpkgdef-utility"></a>Utilidad CreatePkgDef
Toma un archivo. dll para una extensión de Visual Studio como parámetro y crea un archivo *. pkgdef* para acompañar el archivo *. dll* . El archivo *. pkgdef* contiene toda la información que, de lo contrario, se escribiría en el registro del sistema cuando se instala la extensión.

> [!NOTE]
> La mayoría de las plantillas de proyecto que se incluyen en el SDK de Visual Studio crean automáticamente archivos *. pkgdef* como parte del proceso de compilación. Este documento está destinado a aquellos que desean crear paquetes manualmente, o convertir paquetes existentes para usar la implementación de *. pkgdef*  .

## <a name="syntax"></a>Sintaxis

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumentos
**/out = &lt; nombre de archivo&gt;**\
Necesario. Establece el nombre del archivo de salida *. pkgdef* en &lt; filename &gt; .

**/codebase**\
Opcional. Fuerza el registro con la utilidad **codebase** .

**/Assembly**\
Fuerza el registro con la utilidad de **ensamblado** .

**&lt;AssemblyPath&gt;**\
La ruta de acceso del archivo *. dll* desde el que desea generar el archivo *. pkgdef*.

## <a name="remarks"></a>Notas
La implementación de extensiones mediante archivos *. pkgdef* reemplaza los requisitos del registro de versiones anteriores de Visual Studio.

::: moniker range=">=vs-2019"

Los archivos *. pkgdef* deben instalarse en una de las siguientes ubicaciones:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Si la carpeta de instalación es *%LocalAppData%\Microsoft\Visual \\ Studio\16.0\Extensions*, Visual Studio reconoce la extensión, pero está deshabilitada de forma predeterminada. El usuario puede habilitar la extensión mediante el uso de **administrar extensiones**.

Si la carpeta de instalación *es \\ %VSInstallDir%\Common7\IDE\Extensions*, la extensión está habilitada de forma predeterminada.

> [!NOTE]
> La herramienta **administrar extensiones** no se puede usar para tener acceso a una extensión a menos que se instale como parte de un paquete VSIX.

::: moniker-end

::: moniker range="vs-2017"

Los archivos *. pkgdef* deben instalarse en una de las siguientes ubicaciones:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Si la carpeta de instalación es *%LocalAppData%\Microsoft\Visual \\ Studio\15.0\Extensions*, Visual Studio reconoce la extensión, pero está deshabilitada de forma predeterminada. El usuario puede habilitar la extensión mediante **extensiones y actualizaciones**.

Si la carpeta de instalación *es \\ %VSInstallDir%\Common7\IDE\Extensions*, la extensión está habilitada de forma predeterminada.

> [!NOTE]
> No se puede usar la herramienta **extensiones y actualizaciones** para tener acceso a una extensión a menos que se instale como parte de un paquete VSIX.

::: moniker-end

## <a name="see-also"></a>Vea también
- [Utilidad CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
