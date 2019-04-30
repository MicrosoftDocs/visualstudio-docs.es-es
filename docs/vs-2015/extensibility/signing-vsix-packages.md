---
title: Firma de paquetes VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fabe2931310b97f0c0864ea77ceef024f0e57cd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447208"
---
# <a name="signing-vsix-packages"></a>Firma de paquetes VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ensamblados de extensión no es necesario que se firmen antes de que puede ejecutar en Visual Studio, pero es una buena práctica para hacerlo.  
  
 Si desea proteger su extensión y asegúrese de que no se ha manipulado, puede agregar una firma digital a un paquete VSIX. Cuando se firma un archivo VSIX, el instalador de VSIX mostrará un mensaje que indica que está firmado, además de obtener más información acerca de la propia firma. Si se ha modificado el contenido de la extensión VSIX y la extensión VSIX no se ha firmado nuevamente, el instalador de VSIX mostrará que la firma no es válida. No se detiene la instalación, pero se advierte al usuario.  
  
> [!IMPORTANT]
> A partir de 2015, se identificarán los paquetes VSIX firmados mediante algo distinto de cifrado de SHA256 como si tuviera una firma no válida. Instalación de VSIX no está bloqueada, pero se le avisará al usuario.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Firma un archivo VSIX con VSIXSignTool  
 Una herramienta disponible en la firma tiene cifrado SHA256 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) en nuget.org en [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Para usar el VSIXSignTool  
  
1. Agregar el proyecto de VSIX a un proyecto.  
  
2. Haga clic con el botón derecho en el nodo del proyecto en el Explorador de soluciones, seleccionando **agregar &#124; administrar paquetes de NuGet**.  Para obtener más información sobre NuGet y la incorporación de NuGet, paquetes vea [información general sobre NuGet](http://docs.nuget.org/) y [administrar paquetes de NuGet mediante el cuadro de diálogo](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3. Busque VSIXSignTool desde VisualStudioExtensibility e instale el paquete de NuGet.  
  
4. Ahora puede ejecutar el VSIXSignTool desde la ubicación de los paquetes locales del proyecto. Consulte la Ayuda de línea de comandos de la herramienta para su escenario de firma (VSIXSignTool.exe /?).  
  
   Por ejemplo, para iniciar sesión con una contraseña protegido el archivo de certificado:  
  
   /F de inicio de sesión VSIXSignTool.exe \<certfile > /p \<contraseña > \<VSIXfile >  
  
## <a name="see-also"></a>Vea también  
 [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
