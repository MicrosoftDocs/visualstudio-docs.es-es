---
title: Firma de paquetes VSIX | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5a27b4e76e0cd8f986441778ed39c7fbb5a2211
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="signing-vsix-packages"></a>Firma de paquetes VSIX
No es necesario que los ensamblados de extensión se firmen antes de que puede ejecutar en Visual Studio, pero es recomendable hacerlo.  
  
 Si desea proteger la extensión y asegúrese de que no se ha manipulado, puede agregar una firma digital a un paquete VSIX. Cuando se firma un VSIX, el instalador VSIX mostrará un mensaje que indica que está firmado, además de obtener más información sobre la firma propiamente dicha. Si se ha modificado el contenido de la extensión VSIX y la extensión VSIX no ha sido firmada nuevo, el instalador VSIX mostrará que la firma no es válida. No se ha detenido la instalación, pero se advierte al usuario.  
  
> [!IMPORTANT]
>  A partir de 2015, los paquetes VSIX firmados con algo distinto de cifrado SHA256 se identificará como si tuviera una firma no válida. No se bloquea la instalación de VSIX, pero el usuario recibirá una advertencia.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Firma una VSIX con VSIXSignTool  
 Hay un cifrado SHA256 firma herramienta disponible en [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) en nuget.org en [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Para usar el VSIXSignTool  
  
1.  Agregue su VSIX a un proyecto.  
  
2.  Haga clic con el botón secundario en el nodo de proyecto en el Explorador de soluciones, seleccione **Agregar &#124; Administrar paquetes de NuGet**.  Para obtener más información sobre NuGet y agregar consulte paquetes de NuGet, consulte el [documentación de NuGet](http://docs.microsoft.com/NuGet) y [UI del Administrador de paquetes](http://docs.microsoft.com/NuGet/Tools/Package-Manager-UI) temas.  
  
3.  Busque VSIXSignTool de VisualStudioExtensibility e instale el paquete de NuGet.  
  
4.  Ahora puede ejecutar la VSIXSignTool de ubicación de paquetes locales del proyecto. Consulte la Ayuda de línea de comandos de la herramienta para su escenario de firma (VSIXSignTool.exe /?).  
  
 Por ejemplo, para iniciar sesión con una contraseña protegido el archivo de certificado:  
  
 /F de inicio de sesión de VSIXSignTool.exe \<archivoDeCertificado > /p \<contraseña > \<VSIXfile >  
  
## <a name="see-also"></a>Vea también  
 [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)