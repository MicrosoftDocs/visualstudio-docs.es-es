---
title: Utilidad CreatePkgDef | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96b0343cd088a8d608cd3503162bf7fa737b79f4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602447"
---
# <a name="createpkgdef-utility"></a>Utilidad CreatePkgDef
Toma un archivo .dll para una extensión de Visual Studio como un parámetro y crea un *.pkgdef* archivo para acompañar la *.dll* archivo. El *.pkgdef* archivo contiene toda la información en caso contrario, se escribiría en el registro del sistema cuando se instala la extensión.

> [!NOTE]
>  La mayoría de las plantillas de proyecto que se incluyen automáticamente en el SDK de Visual Studio cree *.pkgdef* archivos como parte del proceso de compilación. Este documento está pensado para aquellos que deseen crear manualmente paquetes o convertir los paquetes existentes para usar *.pkgdef* implementación.

## <a name="syntax"></a>Sintaxis

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumentos
 **/ out =&lt;FileName&gt;**  necesarios. Establece el nombre de la *.pkgdef* archivo de salida &lt;FileName&gt;.

 **/CODEBASE** opcional. Fuerza el registro con el **CodeBase** utilidad.

 **/Assembly** fuerza el registro con el **ensamblado** utilidad.

 **&lt;AssemblyPath&gt;**  la ruta de acceso de la *.dll* archivo desde el que desea generar el *.pkgdef*.

## <a name="remarks"></a>Comentarios
 Implementación de extensión mediante el uso de *.pkgdef* archivos reemplaza los requisitos del registro de versiones anteriores de Visual Studio.

 El *.pkgdef* archivos deben estar instalados en una de las siguientes ubicaciones:

- *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

  Si la carpeta de instalación es *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*, la extensión de Visual Studio reconocerá, pero se deshabilitará de forma predeterminada. El usuario puede habilitar la extensión mediante **extensiones y actualizaciones**.

  Si la carpeta de instalación es *%vsinstalldir%\Common7\IDE\Extensions\\*, la extensión está habilitada de forma predeterminada.

> [!NOTE]
>  El **extensiones y actualizaciones** herramienta no puede utilizarse para tener acceso a una extensión a menos que se instala como parte de un paquete VSIX.

## <a name="see-also"></a>Vea también
- [CreateExpInstance utility](../../extensibility/internals/createexpinstance-utility.md)