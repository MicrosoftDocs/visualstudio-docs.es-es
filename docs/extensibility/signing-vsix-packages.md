---
title: Firma de paquetes VSIX ? Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700089"
---
# <a name="signing-vsix-packages"></a>Firma de paquetes VSIX
No es necesario firmar ensamblados de extensión para poder ejecutarse en Visual Studio, pero es recomendable hacerlo.

 Si desea proteger la extensión y asegurarse de que no se ha manipulado, puede agregar una firma digital a un paquete VSIX. Cuando se firma un VSIX, el instalador de VSIX mostrará un mensaje que indica que está firmado, además de más información sobre la propia firma. Si se ha modificado el contenido de VSIX y vSIX no se ha firmado de nuevo, el instalador de VSIX mostrará que la firma no es válida. La instalación no se detiene, pero se advierte al usuario.

> [!IMPORTANT]
> A partir de Visual Studio 2015, los paquetes VSIX firmados con cualquier cosa que no sea el cifrado SHA256 se identificarán como que tienen una firma no válida. La instalación de VSIX no está bloqueada, pero se advertirá al usuario.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Firma de un VSIX con VSIXSignTool
 Hay una herramienta de firma de cifrado SHA256 disponible en [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) en nuget.org en [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Para usar VSIXSignTool

1. Agregue su VSIX a un proyecto.

2. Haga clic con el botón derecho en el nodo del proyecto en el Explorador de soluciones, **seleccionando Agregar &#124; Administrar paquetes NuGet**.  Para obtener más información sobre NuGet y agregar paquetes NuGet, consulte la documentación de [NuGet](/NuGet) y los temas de [interfaz](/NuGet/Tools/Package-Manager-UI) de usuario del Administrador de paquetes.

3. Busque VSIXSignTool en VisualStudioExtensibility e instale el paquete NuGet.

4. Ahora puede ejecutar VSIXSignTool desde la ubicación de paquetes locales del proyecto. Consulte la ayuda de la línea de comandos de la herramienta para su escenario de firma (VSIXSignTool.exe /?).

   Por ejemplo, para firmar con un archivo de certificado protegido por contraseña:

   VSIXSignTool.exe sign \</f certfile \<> \</p password> VSIXfile>

## <a name="see-also"></a>Vea también
- [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
