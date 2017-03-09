---
title: "Administraci&#243;n del cuadro de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Cuadro de herramientas [SDK de Visual Studio], selección automática de pestaña"
  - "Cuadro de herramientas [Visual Studio SDK], administración"
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
caps.handback.revision: 33
manager: "douge"
---
# Administraci&#243;n del cuadro de herramientas
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permite un VSPackage como, por ejemplo, un editor o diseñador, para administrar la pertenencia y la apariencia del **Cuadro de herramientas**.  
  
 Además, el **Cuadro de herramientas** sí puede administrarse mediante la automatización. Para más información sobre la administración de un cuadro de herramientas mediante automatización, vea [Cómo: Controlar el Cuadro de herramientas](../Topic/How%20to:%20Control%20the%20Toolbox.md).  
  
## Selección automática de la pestaña Cuadro de herramientas  
 Es posible activar de manera automática una categoría o pestaña **Cuadro de herramientas** determinada en función del diseñador o editor actualmente activo. Por ejemplo, si se activa un diseñador de formularios, puede que desee seleccionar la pestaña **Todos los formularios Windows Forms**.  
  
 Esto se admite solo para editores y diseñadores que requieran lo siguiente:  
  
1.  Implementar un objeto de fábrica para proporcionar instancias del editor o diseñador. Para más información sobre la implementación de un objeto de generador de diseñador o editor, vea [Generadores de editores](../extensibility/editor-factories.md).  
  
2.  Registrar la pestaña del cuadro de herramientas activada automáticamente si está presente el editor o diseñador.  
  
## Control del cuadro de herramientas  
 Como complemento a la compatibilidad de automatización, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona las siguientes interfaces para proporcionar a VSPackages mayor control sobre la administración del **Cuadro de herramientas**.  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Permite a las aplicaciones administrar, agregar y quitar objetos <xref:System.Drawing.Design.ToolboxItem> desde el **Cuadro de herramientas**. También permite configurar el aspecto y las categorías del **Cuadro de herramientas**.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Permite a las aplicaciones administrar, agregar y quitar controles del **Cuadro de herramientas** basados en la actividad, así como configurar el aspecto y las categorías del **Cuadro de herramientas**.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Extiende la funcionalidad de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> proporcionando compatibilidad para la persistencia y la localización.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Hay varios aspectos importantes que se deben tener en cuenta al trabajar con estas interfaces:  
  
-   <xref:System.Drawing.Design.IToolboxService> solo está disponible para VSPackages basados en Managed Package Framework.  
  
-   No se pueden agregar controles directamente al **Cuadro de herramientas** mediante <xref:System.Drawing.Design.IToolboxService>.  
  
-   Un VSPackage debe usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> para agregar controles o para hospedar el control en un control contenedor que se deriva de <xref:System.Windows.Forms.AxHost>.  
  
     Visual Studio proporciona la herramienta `Aximp.exe` para automatizar el ajuste de un control de ActiveX en un control derivado de <xref:System.Windows.Forms.AxHost>. Para obtener más información, consulta [Aximp.exe \(Windows Forms ActiveX Control Importer\)](../Topic/Aximp.exe%20\(Windows%20Forms%20ActiveX%20Control%20Importer\).md).  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> son interfaces de COM que están disponibles a través de los ensamblados de interoperabilidad.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> se deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> e implementa todos sus métodos.  
  
     Los objetos solo obtienen una instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> no se deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y no implementa sus métodos.  
  
     Los objetos que necesitan funcionalidad en ambas interfaces deben obtener instancias de ambas interfaces del entorno.  
  
-   Cuando se trabaja con <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, información sobre los nombres canónicos \(no localizados\) de las pestañas se controla con los métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A>.  
  
-   Al usar <xref:System.Drawing.Design.IToolboxService>, es responsabilidad del implementador administrar la información localizada como, por ejemplo, los nombres de las categorías.  
  
 Use el mecanismo de configuración para permitir a los usuarios guardar la configuración del **Cuadro de herramientas** al que tienen acceso los usuarios mediante el comando **Opciones para importar o exportar**, que se encuentra en el menú **Herramientas** de IDE. Para más información sobre cómo usar la configuración, vea [Opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md).  
  
## Vea también  
 [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md)