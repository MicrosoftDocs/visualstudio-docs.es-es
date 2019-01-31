---
title: Número de versión de los ensamblados principales y los ensamblados satélite localizados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eb699c7b5ab2aec928bf83ada5dd8824f93f3006
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790144"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Número de versión de los ensamblados principales y los ensamblados satélite localizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La clase <xref:System.Resources.SatelliteContractVersionAttribute> proporciona compatibilidad de versiones para un ensamblado principal que usa recursos localizados mediante el administrador de recursos. Aplicar <xref:System.Resources.SatelliteContractVersionAttribute> al ensamblado principal de una aplicación le permite actualizar y volver a implementar el ensamblado sin actualizar sus ensamblados satélite. Por ejemplo, puede usar la clase <xref:System.Resources.SatelliteContractVersionAttribute> con un Service Pack que no introduce nuevos recursos sin volver a compilar e implementar los ensamblados satélite. Para que los recursos localizados estén disponibles, la versión de contrato satélite del ensamblado principal debe coincidir con la clase <xref:System.Reflection.AssemblyVersionAttribute> de los ensamblados satélite. Debe especificar un número de versión exacto en <xref:System.Resources.SatelliteContractVersionAttribute>; los caracteres comodín como "*" no están permitidos. Para obtener más información, consulte [Recuperar recursos](http://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f).  
  
## <a name="updating-assemblies"></a>Actualizar ensamblados  
 La clase <xref:System.Resources.SatelliteContractVersionAttribute> le permite actualizar un ensamblado principal sin tener que actualizar el ensamblado satélite, o viceversa. Cuando se actualiza el ensamblado principal, se cambia su número de versión de ensamblado. Si quiere seguir usando los ensamblados satélite existentes, cambie el número de versión del ensamblado principal pero deje igual el número de versión del contrato satélite. Por ejemplo, la primera versión del ensamblado principal podría ser 1.0.0.0. La versión de contrato satélite y la versión del ensamblado satélite serán también 1.0.0.0. Si necesita actualizar el ensamblado principal para un Service Pack, puede cambiar la versión de ensamblado a 1.0.0.1, manteniendo la versión de contrato satélite y la versión de ensamblado del satélite como 1.0.0.0.  
  
 Si necesita actualizar un ensamblado satélite pero no el ensamblado principal, cambie el atributo <xref:System.Reflection.AssemblyVersionAttribute> del ensamblado satélite. Junto con el ensamblado satélite, tendrá que distribuir un ensamblado de directiva que indique que el nuevo ensamblado satélite es compatible con el ensamblado satélite antiguo. Para obtener más información sobre directivas, consulte [Cómo el motor en tiempo de ejecución ubica ensamblados](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
 El código siguiente muestra cómo establecer la versión de contrato satélite. El código se puede colocar en un script de compilación o en el archivo AssemblyInfo.vb o AssemblyInfo.cs.  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>Vea también  
 [Cómo el motor en tiempo de ejecución ubica ensamblados](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)   
 [Configurar atributos de ensamblados](http://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e)   
 [Seguridad y ensamblados satélite localizados](../ide/security-and-localized-satellite-assemblies.md)   
 [Localizar aplicaciones](../ide/localizing-applications.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)
