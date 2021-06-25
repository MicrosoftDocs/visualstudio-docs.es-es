---
title: Firma de paquetes VSIX | Microsoft Docs
description: Obtenga información sobre cómo firmar ensamblados de extensión. El instalador de VSIX muestra un mensaje que indica que un VSIX está firmado e información sobre la propia firma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d481c75754c7bc49369987d4bf6dc3aa33e96fdc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899165"
---
# <a name="signing-vsix-packages"></a>Firma de paquetes VSIX
No es necesario firmar los ensamblados de extensión para poder ejecutarse en Visual Studio, pero es un procedimiento recomendado hacerlo.

 Si desea proteger la extensión y asegurarse de que no se ha alterado, puede agregar una firma digital a un paquete VSIX. Cuando se firma un VSIX, el instalador de VSIX mostrará un mensaje que indica que está firmado, además de más información sobre la propia firma. Si se ha modificado el contenido de VSIX y el VSIX no se ha firmado de nuevo, el instalador de VSIX mostrará que la firma no es válida. La instalación no se detiene, pero se advierte al usuario.

> [!IMPORTANT]
> A partir Visual Studio 2015, los paquetes VSIX firmados con un cifrado distinto de SHA256 se identificarán como que tienen una firma no válida. La instalación de VSIX no está bloqueada, pero se advertirá al usuario.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Firmar un VSIX con VSIXSignTool
 Hay una herramienta de firma de cifrado SHA256 disponible en [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) nuget.org en [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Para usar VSIXSignTool

1. Agregue el VSIX a un proyecto.

2. Haga clic con el botón derecho en el nodo del proyecto Explorador de soluciones seleccione **Agregar &#124; administrar paquetes NuGet**.  Para obtener más información sobre NuGet y agregar paquetes NuGet, consulte la documentación de [NuGet](/NuGet) [y los Administrador de paquetes de la interfaz de](/NuGet/Tools/Package-Manager-UI) usuario.

3. Busque VSIXSignTool en VisualStudioExtensibility e instale el paquete NuGet.

4. Ahora puede ejecutar VSIXSignTool desde la ubicación de paquetes locales del proyecto. Consulte la ayuda de la línea de comandos de la herramienta para el escenario de firma (VSIXSignTool.exe /?).

   Por ejemplo, para firmar con un archivo de certificado protegido con contraseña:

   VSIXSignTool.exe /f \<certfile> /p \<password>\<VSIXfile>

## <a name="see-also"></a>Consulta también
- [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
