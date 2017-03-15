---
title: "Informaci&#243;n general de personalizaci&#243;n de marca | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuado de diálogo Acerca de"
  - "VSPackages, pantallas de presentación"
  - "VSPackages, personalización de marca"
ms.assetid: a47b3645-574c-41c7-8a97-d071cd6b1e82
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Informaci&#243;n general de personalizaci&#243;n de marca
Para mostrar información de producto en la pantalla de presentación o el cuadro de diálogo **Ayuda de Acerca de** , el Paquete debe cualquiera:  
  
-   Provide información detallada de producto bajo la clave del Registro de InstalledProducts.  
  
     O bien  
  
-   Implemente<xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  
  
 El \(MPF\) managed package proporciona el atributo de <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> en el registro de control bajo la clave del Registro de InstalledProducts.  Para obtener más información, vea [Cómo: Personalizar la marca de un paquete VSPackage \(C\# y Visual Basic\)](../misc/how-to-brand-a-vspackage-csharp-and-visual-basic.md).  
  
 la biblioteca de Visual Studio proporciona la clase de plantilla de `IVsInstalledProductImpl` para crear una implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  Para obtener más información, vea [Procedimiento: personalizar un VSPackage \(C\+\+\)](../misc/how-to-brand-a-vspackage-cpp.md).  
  
 Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> explícitamente es más eficaz que el atributo o la plantilla.  
  
-   Puede especificar un icono de la pantalla de presentación que difiere del icono de **Ayuda de Acerca de** .  
  
-   Puede especificar un nombre de producto de la pantalla de presentación distinto del nombre de producto de **Ayuda de Acerca de** .  
  
    > [!IMPORTANT]
    >  Si utiliza <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> y también implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>, la interfaz tiene prioridad.  
  
    > [!NOTE]
    >  Utilizan el mismo recurso de icono de la pantalla de presentación y el cuadro de diálogo de **Ayuda de Acerca de** .  El recurso de icono de VSPackage debe incluir 16 una imagen de x 16 para la pantalla de presentación y 32 una imagen de x 32 para el cuadro de diálogo de **Ayuda de Acerca de** .  Si solo se proporciona un tamaño de imagen, se devolverá el tamaño según sea necesario, pero los resultados visuales se subóptimos.  
  
 Para obtener una lista de tareas relacionadas, vea [VSPackages](../extensibility/internals/vspackages.md).  
  
## Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)   
 [Información general de Visual Studio Library](../misc/visual-studio-library-overview.md)