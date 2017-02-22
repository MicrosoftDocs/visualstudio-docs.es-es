---
title: "Registrar y anular el registro VSPackages | Microsoft Docs"
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
  - "registro, VSPackages"
  - "VSPackages, registrar"
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
caps.handback.revision: 35
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrar y anular el registro VSPackages
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizar atributos para registrar un paquete VSPackage, pero  
  
## Registrar un paquete VSPackage  
 Puede usar atributos para controlar el registro de VSPackages administrado. Toda la información de registro se encuentra en un archivo .pkgdef. Para obtener más información sobre el registro de archivo, consulte [Utilidad de CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 El código siguiente muestra cómo utilizar los atributos estándar de registro para registrar el VSPackage.  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## Anular el registro de una extensión  
 Si ha variado con mucha VSPackages diferente y eliminarlos de la instancia experimental, puede ejecutar simplemente el **Restablecer** comando. Busque **Restablecer Visual Studio Experimental Instance** en la página de inicio del equipo, o ejecutar este comando desde la línea de comandos:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Si desea desinstalar una extensión que ha instalado en la instancia de desarrollo de Visual Studio, vaya a **Herramientas \/ extensiones y actualizaciones**, busque la extensión y haga clic en **desinstalar**.  
  
 Si por algún motivo, ninguno de estos métodos es correcta al desinstalar la extensión, puede anular el registro del ensamblado de VSPackage desde la línea de comandos como sigue:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)