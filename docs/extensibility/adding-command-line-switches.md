---
title: Adición de modificadores de línea de comandos | Microsoft Docs
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
ms.openlocfilehash: de0044544a97134380900d3e55f54c8fb34431fd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352334"
---
# <a name="add-command-line-switches"></a>Agregar modificadores de línea de comandos
Puede agregar modificadores de línea de comandos que se aplican a su VSPackage al *devenv.exe* se ejecuta. Use <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> para declarar el nombre del modificador y sus propiedades. En este ejemplo, se agrega el conmutador MySwitch para una subclase de VSPackage llamado **AddCommandSwitchPackage** sin argumentos y con el VSPackage que se cargan automáticamente.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 En las siguientes descripciones se muestran los parámetros con nombre.

||||
|-|-|-|-|
| Parámetro | Descripción|
| Argumentos | El número de argumentos para el conmutador. Puede ser "*", o una lista de argumentos. |
| DemandLoad | Cargar el VSPackage automáticamente si se establece en 1, en caso contrario, se establece en 0. |
| HelpString | La Ayuda de cadena o identificador de recurso de la cadena para mostrar con **devenv /?** . |
| Name | El conmutador. |
| PackageGuid | El GUID del paquete. |

 El primer valor de argumentos es normalmente 0 o 1. Un valor especial de ' *' puede usarse para indicar que el resto de la línea de comandos completo es el argumento. Esto puede ser útil para escenarios donde un usuario debe pasar una cadena de comandos del depurador de depuración.

 Es el valor DemandLoad `true` (1) o `false` (0) indica que se debe cargar automáticamente el VSPackage.

 ¿El valor de HelpString es el identificador de recurso de la cadena que aparece en el **devenv /?** Presentación de la Ayuda. Este valor debe estar en el formulario "#nnn" donde nnn es un entero. El valor de cadena en el archivo de recursos debe acabar con un carácter de nueva línea.

 El valor de nombre es el nombre del conmutador.

 El valor de PackageGuid es el GUID del paquete que implementa este modificador. El IDE usa este GUID para buscar el VSPackage en el registro al que se aplica el modificador de línea de comandos.

## <a name="retrieve-command-line-switches"></a>Recuperar los modificadores de línea de comandos
 Cuando se carga el paquete, puede recuperar los modificadores de línea de comandos mediante los pasos siguientes.

1. En el VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementación, llamada `QueryService` en <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> para obtener el <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfaz.

2. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> para recuperar los modificadores de línea de comandos que el usuario especificado.

   El código siguiente muestra cómo averiguar si se ha especificado el modificador de línea de comandos MySwitch por el usuario:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Es su responsabilidad para comprobar los modificadores de línea de comandos cada vez que se carga el paquete.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)
- [Utilidad CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Archivos pkgdef](/visualstudio/extensibility/shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file)