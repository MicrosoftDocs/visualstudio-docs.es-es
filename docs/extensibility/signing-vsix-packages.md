---
title: "Firma de paquetes VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "firma"
  - "firmar"
  - "Authenticode"
  - "VSIX"
  - "paquetes"
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Firma de paquetes VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ensamblados de extensión no es necesario iniciar sesión antes de que se puede ejecutar en Visual Studio, pero es recomendable hacerlo.  
  
 Si desea proteger su extensión y asegúrese de que no se ha manipulado, puede agregar una firma digital a un paquete VSIX. Cuando se firma un archivo VSIX, el instalador VSIX mostrará un mensaje que indica que está firmado, además de obtener más información acerca de la propia firma. Si se ha modificado el contenido de la extensión VSIX y VSIX no ha firmado nuevamente, el instalador VSIX mostrará que la firma no es válida. La instalación no se detiene, pero se avisa al usuario.  
  
> [!IMPORTANT]
>  A partir de 2015, los paquetes VSIX firmados mediante cifrado SHA256 distinto se identificará como si tuviera una firma no válida. Instalación de VSIX no está bloqueada, pero el usuario recibirá una advertencia.  
  
## Firma un archivo VSIX con VSIXSignTool  
 Una herramienta de firma tiene cifrado SHA256 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) en nuget.org en [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### Usar el VSIXSignTool  
  
1.  Agregue su VSIX a un proyecto.  
  
2.  Haga clic en el nodo de proyecto en el Explorador de soluciones, seleccione **Agregar &#124; Administrar paquetes de NuGet**.  Para obtener más información sobre NuGet y agregar NuGet consulte paquetes [Descripción general de NuGet](http://docs.nuget.org/) y [Administrar paquetes de NuGet mediante el cuadro de diálogo](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3.  VSIXSignTool de VisualStudioExtensibility buscar e instalar el paquete de NuGet.  
  
4.  Ahora puede ejecutar la VSIXSignTool desde la ubicación de los paquetes locales del proyecto. Consulte la Ayuda de línea de comandos de la herramienta para su escenario de firma \(VSIXSignTool.exe \/?\).  
  
 Por ejemplo, para iniciar sesión con una contraseña protegido el archivo de certificado:  
  
 VSIXSignTool.exe inicio de sesión \/f \< certfile \> \/p \< contraseña \>\< VSIXfile \>  
  
## Vea también  
 [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)