---
title: Registrar y anular el registro de VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193815"
---
# <a name="registering-and-unregistering-vspackages"></a>Registro y anulación del registro de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los atributos se usan para registrar un VSPackage, pero  
  
## <a name="registering-a-vspackage"></a>Registrar un VSPackage  
 Puede usar atributos para controlar el registro de los VSPackages administrados. Toda la información de registro se encuentra en un archivo. pkgdef. Para obtener más información sobre el registro basado en archivos, consulte [utilidad CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 En el código siguiente se muestra cómo usar los atributos estándar de registro para registrar el VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Anulación del registro de una extensión  
 Si ha estado experimentando con muchos VSPackages diferentes y desea quitarlos de la instancia experimental, solo puede ejecutar el comando de **restablecimiento** . Busque **restablecer la instancia experimental de Visual Studio** en la página de inicio del equipo o ejecute este comando desde la línea de comandos:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Si desea desinstalar una extensión que ha instalado en la instancia de desarrollo de Visual Studio, vaya a **herramientas/extensiones y actualizaciones**, busque la extensión y haga clic en **desinstalar**.  
  
 Si, por alguna razón, ninguno de estos métodos se ejecuta correctamente en la desinstalación de la extensión, puede anular el registro del ensamblado VSPackage desde la línea de comandos de la siguiente manera:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Consulte también  
 [VSPackages](../extensibility/internals/vspackages.md)
