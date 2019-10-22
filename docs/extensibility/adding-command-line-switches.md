---
title: Agregando modificadores de la línea de comandos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c44864285f3e5701604379a110292c29d3f9b78
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821532"
---
# <a name="add-command-line-switches"></a>Agregar modificadores de la línea de comandos
Puede agregar modificadores de la línea de comandos que se aplican a su VSPackage cuando se ejecuta *devenv. exe* . Use <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> para declarar el nombre del modificador y sus propiedades. En este ejemplo, se agrega el modificador mySwitch para una subclase de VSPackage denominada **AddCommandSwitchPackage** sin argumentos y el VSPackage se carga automáticamente.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Los parámetros con nombre se muestran en las siguientes descripciones.

||||
|-|-|-|-|
| Parámetro | DESCRIPCIÓN|
| Argumentos | El número de argumentos para el modificador. Puede ser "*", o una lista de argumentos. |
| DemandLoad | Cargue el VSPackage automáticamente si se establece en 1; de lo contrario, establézcalo en 0. |
| HelpString | Cadena de ayuda o identificador de recurso de la cadena que se va a mostrar con **devenv/?** . |
| NOMBRE | Modificador. |
| PackageGuid | GUID del paquete. |

 El primer valor de arguments es normalmente 0 o 1. Se puede usar un valor especial de ' * ' para indicar que todo el resto de la línea de comandos es el argumento. Esto puede ser útil para depurar escenarios en los que un usuario debe pasar una cadena de comandos del depurador.

 El valor de DemandLoad es `true` (1) o `false` (0) indica que el VSPackage debe cargarse automáticamente.

 El valor de HelpString es el identificador de recurso de la cadena que aparece en **devenv/?** Pantalla de ayuda. Este valor debe tener el formato "#nnn", donde nnn es un entero. El valor de cadena del archivo de recursos debe terminar en un carácter de nueva línea.

 El valor de Name es el nombre del modificador.

 El valor de PackageGuid es el GUID del paquete que implementa este modificador. El IDE usa este GUID para buscar el VSPackage en el registro al que se aplica el modificador de línea de comandos.

## <a name="retrieve-command-line-switches"></a>Recuperar modificadores de la línea de comandos
 Una vez cargado el paquete, puede recuperar los modificadores de la línea de comandos completando los pasos siguientes.

1. En la implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> VSPackage, llame `QueryService` a <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> en para obtener <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> la interfaz.

2. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> a para recuperar los modificadores de la línea de comandos especificados por el usuario.

   En el código siguiente se muestra cómo averiguar si el modificador de la línea de comandos mySwitch lo ha escrito el usuario:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Es su responsabilidad comprobar los modificadores de la línea de comandos cada vez que se carga el paquete.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)
- [Utilidad CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Archivos Pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)