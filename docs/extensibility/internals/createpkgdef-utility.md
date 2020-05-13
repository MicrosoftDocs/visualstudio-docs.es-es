---
title: Utilidad CreatePkgDef (Utilidad CreatePkgDef) Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709166"
---
# <a name="createpkgdef-utility"></a>Utilidad CreatePkgDef
Toma un archivo .dll para una extensión de Visual Studio como parámetro y crea un archivo *.pkgdef* para acompañar el archivo *.dll.* El archivo *.pkgdef* contiene toda la información que de otro modo se escribiría en el registro del sistema cuando se instala la extensión.

> [!NOTE]
> La mayoría de las plantillas de proyecto que se incluyen en el SDK de Visual Studio crean automáticamente archivos *.pkgdef* como parte del proceso de compilación. Este documento está pensado para aquellos que desean crear paquetes manualmente o convertir paquetes existentes para usar la implementación *.pkgdef.*

## <a name="syntax"></a>Sintaxis

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumentos
**/out-&lt;NombredeArchivo&gt;**\
Necesario. Establece el nombre del archivo de &lt;salida&gt; *.pkgdef* en FileName .

**/codebase**\
Opcional. Fuerza el registro con la utilidad **CodeBase.**

**/ensamblaje**\
Fuerza el registro con la utilidad **Asamblea.**

**&lt;AssemblyPath&gt;**\
La ruta de acceso del archivo *.dll* desde el que desea generar el *archivo .pkgdef*.

## <a name="remarks"></a>Observaciones
La implementación de extensiones mediante archivos *.pkgdef* reemplaza los requisitos del Registro de versiones anteriores de Visual Studio.

::: moniker range=">=vs-2019"

Los archivos *.pkgdef* deben instalarse en una de las siguientes ubicaciones:

- *%localappdata%-Microsoft-Visual Studio-16.0-Extensiones\\*

- *%vsinstalldir%-Common7-IDE-Extensiones\\*

Si la carpeta de instalación es *%localappdata%-Microsoft-Visual\\Studio-16.0-Extensions*, visual Studio reconoce la extensión, pero está deshabilitada de forma predeterminada. El usuario puede habilitar la extensión mediante **Administrar extensiones**.

Si la carpeta de instalación es *%vsinstalldir%-Common7-IDE-Extensions\\*, la extensión está habilitada de forma predeterminada.

> [!NOTE]
> La herramienta **Administrar extensiones** no se puede usar para tener acceso a una extensión a menos que se instale como parte de un paquete VSIX.

::: moniker-end

::: moniker range="vs-2017"

Los archivos *.pkgdef* deben instalarse en una de las siguientes ubicaciones:

- *%localappdata%-Microsoft-Visual Studio-15.0-Extensiones\\*

- *%vsinstalldir%-Common7-IDE-Extensiones\\*

Si la carpeta de instalación es *%localappdata%-Microsoft-Visual\\Studio-15.0-Extensions*, Visual Studio reconoce la extensión, pero está deshabilitada de forma predeterminada. El usuario puede habilitar la extensión mediante **Extensiones y actualizaciones**.

Si la carpeta de instalación es *%vsinstalldir%-Common7-IDE-Extensions\\*, la extensión está habilitada de forma predeterminada.

> [!NOTE]
> La herramienta **Extensiones y actualizaciones** no se puede utilizar para tener acceso a una extensión a menos que se instale como parte de un paquete VSIX.

::: moniker-end

## <a name="see-also"></a>Vea también
- [Utilidad CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
