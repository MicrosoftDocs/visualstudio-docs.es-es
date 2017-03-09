---
title: "N&#250;mero de versi&#243;n de los ensamblados principales y los ensamblados sat&#233;lite localizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ensamblados [Visual Studio], números de versión"
  - "ensamblados satélite, números de versión"
  - "SatelliteContractVersionAttribute"
  - "números de versión, ensamblados"
  - "control de versiones, ensamblados"
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# N&#250;mero de versi&#243;n de los ensamblados principales y los ensamblados sat&#233;lite localizados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La clase <xref:System.Resources.SatelliteContractVersionAttribute> proporciona compatibilidad de versiones para un ensamblado principal que utiliza recursos localizados mediante un administrador de recursos.  Aplicar el atributo <xref:System.Resources.SatelliteContractVersionAttribute> al ensamblado principal de una aplicación permite actualizar y volver a implementar el ensamblado sin necesidad de actualizar sus ensamblados satélite.  Por ejemplo, se puede utilizar la clase <xref:System.Resources.SatelliteContractVersionAttribute> con un Service Pack que no introduce nuevos recursos sin recompilar e implementar los ensamblados satélite.  Para que estén disponibles los recursos localizados, la versión de contrato satélite del ensamblado principal debe coincidir con la clase <xref:System.Reflection.AssemblyVersionAttribute> de los ensamblados satélite.  Debe especificar un número de versión exacto en el <xref:System.Resources.SatelliteContractVersionAttribute>; no se permiten caracteres comodín como "\*".  Para obtener más información, vea [Recuperar recursos](../Topic/Retrieving%20Resources%20in%20Desktop%20Apps.md).  
  
## Actualizar ensamblados  
 La clase <xref:System.Resources.SatelliteContractVersionAttribute> le permite actualizar un ensamblado principal sin tener que actualizar el ensamblado satélite o viceversa.  Cuando se actualiza el ensamblado principal, cambia su número de versión de ensamblado.  Si desea seguir utilizando los ensamblados satélite existentes, cambie el número de versión del ensamblado principal, pero deje intacto el número de versión del contrato satélite.  Por ejemplo, en su primera versión, la versión de ensamblado principal podría ser 1.0.0.0.  La versión de contrato satélite y la versión de ensamblado del ensamblado satélite también será 1.0.0.0.  Si tiene que actualizar el ensamblado principal para un Service Pack, puede cambiar la versión de ensamblado a 1.0.0.1, a la vez que conserva la versión de contrato satélite y la versión de ensamblado del satélite como 1.0.0.0.  
  
 Si debe actualizar un ensamblado satélite pero no el ensamblado principal, cambie el <xref:System.Reflection.AssemblyVersionAttribute> del ensamblado satélite.  Junto con el ensamblado satélite, tendrá que incluir una directiva de ensamblado que confirme que el nuevo ensamblado satélite es compatible con el antiguo ensamblado satélite.  Para obtener más información sobre directivas, vea [Cómo localiza ensamblados el motor de ejecución](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
 En el código siguiente se muestra cómo establecer la versión de contrato satélite.  El código se puede incluir en un script de compilación o en el archivo AssemblyInfo.vb o AssemblyInfo.cs.  
  
```vb#  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```c#  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## Vea también  
 [Cómo el motor en tiempo de ejecución ubica ensamblados](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md)   
 [Configurar atributos de ensamblados](../Topic/Setting%20Assembly%20Attributes.md)   
 [Seguridad y ensamblados satélite localizados](../ide/security-and-localized-satellite-assemblies.md)   
 [Localizar aplicaciones](../ide/localizing-applications.md)   
 [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)