---
title: Adición de conmutadores de línea de comandos (Command-Line Switches) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740167"
---
# <a name="add-command-line-switches"></a>Agregar modificadores de línea de comandos
Puede agregar modificadores de línea de comandos que se aplican a su VSPackage cuando se ejecuta *devenv.exe.* Se <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> utiliza para declarar el nombre del modificador y sus propiedades. En este ejemplo, el modificador MySwitch se agrega para una subclase de VSPackage denominada **AddCommandSwitchPackage** sin argumentos y con el VSPackage cargado automáticamente.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Los parámetros con nombre se muestran en las descripciones siguientes.

||||
|-|-|-|-|
| Parámetro | Descripción|
| Argumentos | El número de argumentos para el switch. Puede ser "*", o una lista de argumentos. |
| DemandLoad | Cargue el VSPackage automáticamente si se establece en 1, de lo contrario se establece en 0. |
| HelpString | La cadena de ayuda o el identificador de recurso de la cadena que se va a mostrar con **devenv /?**. |
| Nombre | El interruptor. |
| PackageGuid | Identificador único global (GUID) del paquete. |

 El primer valor de Arguments suele ser 0 o 1. Se puede utilizar un valor especial de '*' para indicar que el argumento es el resto de la línea de comandos. Esto puede ser útil para depurar escenarios donde un usuario debe pasar una cadena de comandos del depurador.

 El demandLoad valor `true` es (1) o `false` (0) indica que el VSPackage debe cargarse automáticamente.

 El valor HelpString es el identificador de recurso de la cadena que aparece en el **devenv /?** Pantalla de ayuda. Este valor debe tener la forma "#nnn" donde nnn es un entero. El valor de cadena en el archivo de recursos debe terminar en un nuevo carácter de línea.

 El valor Name es el nombre del switch.

 El valor PackageGuid es el GUID del paquete que implementa este modificador. El IDE usa este GUID para buscar el VSPackage en el registro al que se aplica el modificador de línea de comandos.

## <a name="retrieve-command-line-switches"></a>Recuperar conmutadores de línea de comandos
 Cuando se carga el paquete, puede recuperar los modificadores de línea de comandos completando los pasos siguientes.

1. En la implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> de `QueryService` VSPackage, llame <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> para obtener la <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfaz.

2. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> para recuperar los switches de línea de comandos que el usuario ingresó.

   El código siguiente muestra cómo averiguar si el usuario ha introducido el modificador de línea de comandos MySwitch:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Es su responsabilidad comprobar si los conmutadores de línea de comandos cambian cada vez que se carga el paquete.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)
- [Utilidad CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Archivos Pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
