---
title: "Procedimiento: personalizar un VSPackage (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de diálogo Acerca de"
  - "VSPackages, pantallas de presentación"
  - "VSPackages, personalización de marca"
ms.assetid: a1b9213f-8702-4716-8623-cd3705d531fa
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# Procedimiento: personalizar un VSPackage (C++)
Aparezcan en el cuadro de diálogo de **Ayuda de Acerca de** y la pantalla de presentación, VSPackages debe implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> .  Ello se proporciona la información siguiente a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Name  
  
-   Identificador, como serie o número de versión  
  
-   Información  
  
-   Icono de logotipo  
  
 La clase de `IVsInstalledProductImpl` toma los parámetros de plantilla para esa información.  Cada parámetro de plantilla es un identificador  Los tres primeros son id. de los recursos de cadena y la cuarta es el Id. de recurso de un icono.  
  
## Ejemplo  
 La siguiente declaración de clase para la clase de VSPackage es de [Muestras de VSSDK](../misc/vssdk-samples.md).  
  
```  
class ATL_NO_VTABLE BasicPackage :   
  ...  
  public IVsInstalledProductImpl<  
    IDS_BASICPACKAGE_PRODUCT_NAME,  
    IDS_BASICPACKAGE_PRODUCT_IDENTIFIER,   
    IDS_BASICPACKAGE_PRODUCT_DETAILS,   
    IDI_BASICPACKAGE_LOGO>  
```  
  
 Para probar el Paquete, vea [Cómo: probar la pantalla Ayuda \- Acerca de y la pantalla de presentación](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## Vea también  
 [Personalización de marca de VSPackage](../misc/vspackage-branding.md)