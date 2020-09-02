---
title: Administrar el cuadro de herramientas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 5eeb5d06b0e689391f450fec8744fa58a41f4508
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681540"
---
# <a name="managing-the-toolbox"></a>Managing the Toolbox
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] permite un VSPackage como, por ejemplo, un editor o diseñador, para administrar la pertenencia y la apariencia del **Cuadro de herramientas**.  
  
 Además, el **Cuadro de herramientas** sí puede administrarse mediante la automatización. Para más información sobre la administración de un cuadro de herramientas mediante automatización, vea [How to: Control the Toolbox](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Selección automática de la pestaña Cuadro de herramientas  
 Es posible activar de manera automática una categoría o pestaña **Cuadro de herramientas** determinada en función del diseñador o editor actualmente activo. Por ejemplo, si se activa un diseñador de formularios, puede que desee seleccionar la pestaña **Todos los formularios Windows Forms** .  
  
 Esto se admite solo para editores y diseñadores que requieran lo siguiente:  
  
1. Implementar un objeto de fábrica para proporcionar instancias del editor o diseñador. Para más información sobre la implementación de un objeto de generador de diseñador o editor, vea [Editor Factories](../extensibility/editor-factories.md).  
  
2. Registrar la pestaña del cuadro de herramientas activada automáticamente si está presente el editor o diseñador.  
  
## <a name="controlling-the-toolbox"></a>Control del cuadro de herramientas  
 Como complemento a la compatibilidad de automatización, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] proporciona las siguientes interfaces para proporcionar a VSPackages mayor control sobre la administración del **Cuadro de herramientas** .  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Permite a las aplicaciones administrar, agregar y quitar <xref:System.Drawing.Design.ToolboxItem> objetos del **cuadro de herramientas**. También permite configurar el aspecto y las categorías del **Cuadro de herramientas** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Permite a las aplicaciones administrar, agregar y quitar controles del **Cuadro de herramientas** basados en la actividad, así como configurar el aspecto y las categorías del **Cuadro de herramientas** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Extiende la funcionalidad de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> proporcionando compatibilidad para la persistencia y la localización.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Hay varios aspectos importantes que se deben tener en cuenta al trabajar con estas interfaces:  
  
- <xref:System.Drawing.Design.IToolboxService> solo está disponible para VSPackages basados en Managed Package Framework.  
  
- Los controles no se pueden agregar directamente al **cuadro de herramientas** mediante <xref:System.Drawing.Design.IToolboxService> .  
  
- Un VSPackage debe usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> para agregar controles o para hospedar el control en un control contenedor que se deriva de <xref:System.Windows.Forms.AxHost>.  
  
   Visual Studio proporciona la herramienta `Aximp.exe` para automatizar el ajuste de un control de ActiveX en un control derivado de <xref:System.Windows.Forms.AxHost>. Para obtener más información, vea [Aximp.exe (Windows Forms importador de controles ActiveX)](https://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> son interfaces de COM que están disponibles a través de los ensamblados de interoperabilidad.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> se deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> e implementa todos sus métodos.  
  
   Los objetos solo obtienen una instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> no se deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y no implementa sus métodos.  
  
   Los objetos que necesitan funcionalidad en ambas interfaces deben obtener instancias de ambas interfaces del entorno.  
  
- Cuando se trabaja con <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, información sobre los nombres canónicos (no localizados) de las pestañas se controla con los métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A>.  
  
- Al usar <xref:System.Drawing.Design.IToolboxService>, es responsabilidad del implementador administrar la información localizada como, por ejemplo, los nombres de las categorías.  
  
  Use el mecanismo de configuración para permitir a los usuarios guardar la configuración del **Cuadro de herramientas** al que tienen acceso los usuarios mediante el comando **Opciones para importar o exportar** , que se encuentra en el menú **Herramientas** de IDE. Para más información sobre cómo usar la configuración, vea [Extending User Settings and Options](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Consulte también  
 [Extensión del cuadro de herramientas](../misc/extending-the-toolbox.md)