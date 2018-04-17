---
title: Adición de modificadores de línea de comandos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: daef07d0b8dd02f6823717b0c0cb5d68d837ccde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="adding-command-line-switches"></a>Adición de modificadores de línea de comandos
Puede agregar modificadores de línea de comandos que se aplican a su VSPackage cuando se ejecuta devenv.exe. Use <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> para declarar el nombre del conmutador y sus propiedades. En este ejemplo, se agrega el modificador MySwitch para una subclase de VSPackage denominado **AddCommandSwitchPackage** sin argumentos y con el VSPackage que se cargan automáticamente.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Los parámetros con nombre se muestran en la tabla siguiente  
  
 Argumentos  
 El número de argumentos para el conmutador. Puede ser "*", o una lista de argumentos.  
  
 DemandLoad  
 El VSPackage se cargan automáticamente, si se establece en 1, de lo contrario se establece en 0.  
  
 HelpString  
 El recurso o la cadena de Id. de Ayuda de la cadena para mostrar con **devenv /?**.  
  
 nombre  
 El conmutador.  
  
 PackageGuid  
 El GUID del paquete.  
  
 El primer valor de argumentos suele ser 0 o 1. Un valor especial de ' *' puede utilizarse para indicar que el resto de la línea de comandos completo es el argumento. Esto puede ser útil para escenarios donde un usuario debe pasar una cadena de comandos del depurador de depuración.  
  
 El valor de DemandLoad sea `true` (1) o `false` (0) indica que se debe cargar automáticamente el VSPackage.  
  
 ¿El valor de HelpString es el identificador de recurso de la cadena que aparece en el devenv /? Presentación de la Ayuda. Este valor debe estar en el formato "#nnn" donde nnn es un entero. El valor de cadena en el archivo de recursos debe acabar con un carácter de nueva línea.  
  
 El valor del nombre es el nombre del conmutador.  
  
 El valor de PackageGuid es el GUID del paquete que implementa este modificador. El IDE usa este GUID para buscar el VSPackage en el registro al que se aplica el modificador de línea de comandos.  
  
## <a name="retrieving-command-line-switches"></a>Recuperar los modificadores de línea de comandos  
 Cuando se carga el paquete, puede completar los pasos siguientes para recuperar los modificadores de línea de comandos.  
  
1.  En el paquete de VS <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación, llamada `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> para obtener el <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfaz.  
  
2.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> para recuperar los modificadores de línea de comandos que el usuario ha escrito.  
  
 El código siguiente muestra cómo averiguar si se ha especificado el modificador de línea de comandos MySwitch por el usuario:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Es su responsabilidad para comprobar si los modificadores de línea de comandos cada vez que se carga el paquete.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)   
 [Utilidad de CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [. Pkgdef archivos](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)