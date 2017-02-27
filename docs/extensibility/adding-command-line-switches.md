---
title: "Agregando modificadores de l&#237;nea de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modificadores de línea de comandos, agregar"
  - "modificadores de línea de comandos, recuperar"
  - "IVsAppCommandLine::GetOption (método)"
  - "modificadores de línea de comandos"
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Agregando modificadores de l&#237;nea de comandos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede agregar los modificadores de línea de comandos que se aplican a su VSPackage cuando se ejecuta devenv.exe. Use <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> para declarar el nombre del conmutador y sus propiedades. En este ejemplo, se agrega el modificador MySwitch para una subclase de VSPackage llamado **AddCommandSwitchPackage** sin argumentos y con el paquete VSPackage que se cargan automáticamente.  
  
```c#  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Los parámetros con nombre se muestran en la tabla siguiente  
  
 Argumentos  
 El número de argumentos para el conmutador. Puede ser "\*", o una lista de argumentos.  
  
 DemandLoad  
 Cargar el VSPackage automáticamente si se establece en 1, en caso contrario, se establece en 0.  
  
 HelpString  
 La Ayuda de cadena o el ID de la cadena para mostrar con **devenv \/?**.  
  
 Nombre  
 El modificador.  
  
 PackageGuid  
 El GUID del paquete.  
  
 El primer valor de los argumentos suele ser 0 o 1. Un valor especial de ' \*' puede usarse para indicar que el resto de la línea de comandos completo es el argumento. Esto puede ser útil para depurar escenarios donde un usuario debe pasar una cadena de comandos del depurador.  
  
 El valor de DemandLoad sea `true` \(1\) o `false` \(0\) indica que se debe cargar automáticamente el VSPackage.  
  
 ¿El valor de HelpString es el identificador de recurso de la cadena que aparece en el devenv \/? Visualización de ayuda. Este valor debe estar en el formato "\#nnn" donde nnn es un entero. El valor de cadena en el archivo de recursos debe acabar con un carácter de nueva línea.  
  
 El valor de nombre es el nombre del conmutador.  
  
 El valor de PackageGuid es el GUID del paquete que implementa este modificador. El IDE usa este GUID para buscar el VSPackage del registro al que se aplica el modificador de línea de comandos.  
  
## Recuperando los modificadores de línea de comandos  
 Cuando se carga el paquete, puede recuperar los modificadores de línea de comandos mediante los pasos siguientes.  
  
1.  En su VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación, llamada `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> para obtener el <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfaz.  
  
2.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> para recuperar los modificadores de línea de comandos que el usuario especificado.  
  
 El código siguiente muestra cómo averiguar si el modificador de línea de comandos MySwitch escrito por el usuario:  
  
```c#  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine)); int isPresent = 0; string optionValue = ""; cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Es responsabilidad suya comprobar los modificadores de línea de comandos cada vez que se carga el paquete.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)   
 [Utilidad de CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [. Archivos pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)