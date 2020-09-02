---
title: Agregando modificadores de la línea de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562281"
---
# <a name="adding-command-line-switches"></a>Adición de modificadores de la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede agregar modificadores de la línea de comandos que se aplican a su VSPackage cuando se ejecuta devenv.exe. Use <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> para declarar el nombre del modificador y sus propiedades. En este ejemplo, se agrega el modificador mySwitch para una subclase de VSPackage denominada **AddCommandSwitchPackage** sin argumentos y el VSPackage se carga automáticamente.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Los parámetros con nombre se muestran en la tabla siguiente.  
  
 Argumentos  
 El número de argumentos para el modificador. Puede ser "*", o una lista de argumentos.  
  
 DemandLoad  
 Cargue el VSPackage automáticamente si se establece en 1; de lo contrario, establézcalo en 0.  
  
 HelpString  
 Cadena de ayuda o identificador de recurso de la cadena que se va a mostrar con **devenv/?**.  
  
 Nombre  
 Modificador.  
  
 PackageGuid  
 Identificador único global (GUID) del paquete.  
  
 El primer valor de arguments es normalmente 0 o 1. Se puede usar un valor especial de ' * ' para indicar que todo el resto de la línea de comandos es el argumento. Esto puede ser útil para depurar escenarios en los que un usuario debe pasar una cadena de comandos del depurador.  
  
 El valor de DemandLoad es `true` (1) o `false` (0) indica que el VSPackage debe cargarse automáticamente.  
  
 El valor de HelpString es el identificador de recurso de la cadena que aparece en devenv/? Pantalla de ayuda. Este valor debe tener el formato "#nnn", donde nnn es un entero. El valor de cadena del archivo de recursos debe terminar en un carácter de nueva línea.  
  
 El valor de Name es el nombre del modificador.  
  
 El valor de PackageGuid es el GUID del paquete que implementa este modificador. El IDE usa este GUID para buscar el VSPackage en el registro al que se aplica el modificador de línea de comandos.  
  
## <a name="retrieving-command-line-switches"></a>Recuperar modificadores de la línea de comandos  
 Una vez cargado el paquete, puede recuperar los modificadores de la línea de comandos completando los pasos siguientes.  
  
1. En la implementación del VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> , llame a `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> para obtener la <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfaz.  
  
2. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> a para recuperar los modificadores de la línea de comandos especificados por el usuario.  
  
   En el código siguiente se muestra cómo averiguar si el modificador de la línea de comandos mySwitch lo ha escrito el usuario:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Es su responsabilidad comprobar los modificadores de la línea de comandos cada vez que se carga el paquete.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Modificadores de línea de comandos de devenv](../ide/reference/devenv-command-line-switches.md)   
 [Utilidad CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [Archivos .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
