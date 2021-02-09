---
title: Firma de paquetes VSIX | Microsoft Docs
description: Más información sobre la firma de ensamblados de extensión. El instalador de VSIX muestra un mensaje que indica que se ha firmado un VSIX e información sobre la propia firma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a0127b16438191a7d4f10ebf351b697455f72b16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928034"
---
# <a name="signing-vsix-packages"></a>Firma de paquetes VSIX
No es necesario que los ensamblados de extensión estén firmados antes de que se puedan ejecutar en Visual Studio, pero es recomendable hacerlo.

 Si desea proteger la extensión y asegurarse de que no se ha manipulado, puede Agregar una firma digital a un paquete VSIX. Cuando se firma VSIX, el instalador de VSIX mostrará un mensaje que indica que está firmado, además de más información sobre la propia firma. Si se ha modificado el contenido de VSIX y el VSIX no se ha firmado de nuevo, el instalador de VSIX mostrará que la firma no es válida. La instalación no se detiene, pero se advierte al usuario.

> [!IMPORTANT]
> A partir de Visual Studio 2015, los paquetes VSIX firmados con cualquier otro que no sea el cifrado SHA256 se identificarán como si tuvieran una firma no válida. No se bloquea la instalación de VSIX, pero se advierte al usuario.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Firmar un VSIX con VSIXSignTool
 Hay una herramienta de firma de cifrado SHA256 disponible en [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) en Nuget.org en [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Para usar VSIXSignTool

1. Agregue VSIX a un proyecto.

2. Haga clic con el botón derecho en el nodo del proyecto en Explorador de soluciones, seleccionando **agregar &#124; administrar paquetes NuGet**.  Para más información sobre NuGet y la adición de paquetes NuGet, consulte los temas de la [documentación de Nuget](/NuGet) y del [Administrador de paquetes](/NuGet/Tools/Package-Manager-UI) .

3. Busque VSIXSignTool desde VisualStudioExtensibility e instale el paquete NuGet.

4. Ahora puede ejecutar VSIXSignTool desde la ubicación de paquetes locales del proyecto. Consulte la ayuda de la línea de comandos de la herramienta para su escenario de firma (VSIXSignTool.exe/?).

   Por ejemplo, para firmar con un archivo de certificado protegido por contraseña:

   VSIXSignTool.exe signo/f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Vea también
- [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
