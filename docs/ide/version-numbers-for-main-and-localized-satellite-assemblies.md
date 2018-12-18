---
title: Número de versión de los ensamblados principales y los ensamblados satélite localizados
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cbc74d746453c5d8e60161004a5b56a2c21915dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882611"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Número de versión de los ensamblados principales y los ensamblados satélite localizados
La clase <xref:System.Resources.SatelliteContractVersionAttribute> proporciona compatibilidad de versiones para un ensamblado principal que usa recursos localizados mediante el Administrador de recursos. La aplicación de <xref:System.Resources.SatelliteContractVersionAttribute> al ensamblado principal de una aplicación permite actualizar y volver a implementar el ensamblado sin actualizar sus ensamblados satélite. Por ejemplo, puede usar la clase <xref:System.Resources.SatelliteContractVersionAttribute> con un Service Pack que no introduce nuevos recursos sin volver a compilar e implementar los ensamblados satélite. Para que los recursos localizados estén disponibles, la versión de contrato satélite del ensamblado principal debe coincidir con la clase <xref:System.Reflection.AssemblyVersionAttribute> de los ensamblados satélite. Especifique un número de versión exacto en <xref:System.Resources.SatelliteContractVersionAttribute>; los caracteres comodín como "*" no están permitidos. Para obtener más información, consulte [Recuperar recursos](/dotnet/framework/resources/retrieving-resources-in-desktop-apps).

## <a name="update-assemblies"></a>Actualizar ensamblados
 La clase <xref:System.Resources.SatelliteContractVersionAttribute> le permite actualizar un ensamblado principal sin tener que actualizar el ensamblado satélite, o viceversa. Cuando se actualiza el ensamblado principal, se cambia su número de versión de ensamblado. Si quiere seguir usando los ensamblados satélite existentes, cambie el número de versión del ensamblado principal pero deje igual el número de versión del contrato satélite. Por ejemplo, la primera versión del ensamblado principal podría ser 1.0.0.0. La versión de contrato satélite y la versión del ensamblado satélite serán también 1.0.0.0. Si necesita actualizar el ensamblado principal para un Service Pack, puede cambiar la versión de ensamblado a 1.0.0.1, manteniendo la versión de contrato satélite y la versión de ensamblado del satélite como 1.0.0.0.

 Si necesita actualizar un ensamblado satélite pero no el ensamblado principal, cambie el atributo <xref:System.Reflection.AssemblyVersionAttribute> del ensamblado satélite. Junto con el ensamblado satélite, tendrá que distribuir un ensamblado de directiva que indique que el nuevo ensamblado satélite es compatible con el ensamblado satélite antiguo. Para obtener más información sobre directivas, consulte [Cómo el motor en tiempo de ejecución ubica ensamblados](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

 El código siguiente muestra cómo establecer la versión de contrato satélite. El código se puede colocar en un script de compilación o en el archivo *AssemblyInfo.vb* o *AssemblyInfo.cs*.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>
```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>Vea también

- [Cómo el motor en tiempo de ejecución ubica ensamblados](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [Establecer atributos de ensamblado](/dotnet/framework/app-domains/set-assembly-attributes)
- [Seguridad y ensamblados satélite localizados](../ide/security-and-localized-satellite-assemblies.md)
- [Localizar aplicaciones](../ide/localizing-applications.md)
- [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)