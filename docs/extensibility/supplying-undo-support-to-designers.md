---
title: "Proporcionando compatibilidad a los diseñadores de deshacer | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98243c15f5f69a9aecba589b966d56a68201ab2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="supplying-undo-support-to-designers"></a>Proporcionar soporte técnico de deshacer para diseñadores
Diseñadores, como editores, normalmente se necesitan admitir las operaciones de deshacer, que los usuarios pueden invertir los cambios recientes cuando se modifica un elemento de código.  
  
 Mayoría de los diseñadores implementada en Visual Studio tiene compatibilidad de deshacer proporciona automáticamente el entorno.  
  
 Implementaciones de diseñadores que necesitan para proporcionar compatibilidad con la característica de deshacer:  
  
-   Proporcionar administración de deshacer mediante la implementación de la clase base abstracta<xref:System.ComponentModel.Design.UndoEngine>  
  
-   Proporcione persistencia y CodeDOM admiten implementando la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> y <xref:System.ComponentModel.Design.IComponentChangeService> clases.  
  
 Para obtener más información sobre cómo escribir diseñadores que utilicen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], consulte [extender compatibilidad en tiempo de diseño](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona una infraestructura de deshacer de forma predeterminada por:  
  
-   Proporciona las implementaciones de administración a través de deshacer la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> y <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> clases.  
  
-   Proporcionando compatibilidad de CodeDOM a través de la opción predeterminada y la persistencia <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> y <xref:System.ComponentModel.Design.IComponentChangeService> las implementaciones.  
  
## <a name="obtaining-undo-support-automatically"></a>Obtener soporte técnico de deshacer automáticamente  
 Cualquier creado en el diseñador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es compatible con reversión automática y completa si es, el diseñador:  
  
-   Hace uso de un <xref:System.Windows.Forms.Control> en función de clase para su interfaz de usuario.  
  
-   Emplea el sistema de análisis y generación de código estándar basada en CodeDOM para la persistencia y la generación de código.  
  
     Para obtener más información sobre cómo trabajar con compatibilidad de CodeDOM de Visual Studio, vea [generación de código fuente dinámico y la compilación](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Cuándo se debe usar la compatibilidad con deshacer diseñador explícita  
 Diseñadores deben proporcionar su propia administración de deshacer si usa una interfaz gráfica de usuario, que se conoce como un adaptador de vista, distinta de la proporcionada por <xref:System.Windows.Forms.Control>.  
  
 Un ejemplo de esto podría crear un producto con una interfaz de diseño gráfico basada en web en lugar de un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] según la interfaz gráfica.  
  
 En tales casos, sería necesario registrar este adaptador de vista con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>y proporcionar administración de deshacer explícita.  
  
 Diseñadores deben proporcionar CodeDOM y persistencia admiten si no utilizan el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de generación de código proporcionado en la <xref:System.CodeDom> espacio de nombres.  
  
## <a name="undo-support-features-of-the-designer"></a>Deshacer las características de compatibilidad del diseñador  
 El SDK de entorno proporciona implementaciones predeterminadas de las interfaces necesarias para proporcionar capacidad que se puede usar los diseñadores no usa para deshacer <xref:System.Windows.Forms.Control> según las clases para sus interfaces de usuario o el modelo CodeDOM y persistencia estándar.  
  
 El <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase se deriva de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> clase usando una implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> clase para administrar las operaciones de deshacer.  
  
 Visual Studio proporciona la siguiente función al diseñador de reversión:  
  
-   Funcionalidad de la acción de deshacer vinculada a través de varios diseñadores.  
  
-   Unidades de secundarios dentro de un diseñador pueden interactuar con sus elementos primarios mediante la implementación <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> en <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 El SDK del entorno proporciona compatibilidad con CodeDOM y persistencia proporcionando:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>como un implementaciones de la<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 A <xref:System.ComponentModel.Design.IComponentChangeService> proporcionada por el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]"host de diseño.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Con las características SDK de entorno para proporcionar compatibilidad con deshacer  
 Para obtener soporte técnico de deshacer, un objeto que implementa un diseñador debe:  
  
-   Crear instancias e inicializar una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase con válido <xref:System.IServiceProvider> implementación.  
  
-   Esto <xref:System.IServiceProvider> clase debe proporcionar los siguientes servicios:  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Diseñadores que utilicen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serialización de CodeDOM puede optar por usar <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> proporcionada con la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] como su implementación de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         En este caso, el <xref:System.IServiceProvider> clase proporcionada para el <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> constructor debería devolver este objeto como una implementación de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> clase.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Diseñadores que utilicen el valor predeterminado <xref:System.ComponentModel.Design.DesignSurface> proporcionada por el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se garantiza que el host de diseño tiene una implementación predeterminada de la <xref:System.ComponentModel.Design.IComponentChangeService> clase.  
  
 Los diseñadores que implementan un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mecanismo basado en Deshacer automáticamente realiza un seguimiento de cambios si:  
  
-   Cambios de propiedad se realizan a través del <xref:System.ComponentModel.TypeDescriptor> objeto.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>eventos se generan manualmente cuando se confirma un cambio que se pueden deshacer.  
  
-   Modificación en el diseñador se creó en el contexto de un <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   El diseñador decide explícitamente crear unidades de deshacer usando la unidad de deshacer estándar proporcionada por una implementación de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> o la implementación específicos de Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, que deriva de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> y también proporciona un implementación de ambos <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Ampliar compatibilidad en tiempo de diseño](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)