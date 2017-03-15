---
title: "Proporcionando compatibilidad a los diseñadores de deshacer | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 95e6873d0a3b254fa8f34144253a44c0a8cab60d
ms.lasthandoff: 02/22/2017

---
# <a name="supplying-undo-support-to-designers"></a>Proporciona compatibilidad de deshacer para diseñadores
Diseñadores, como editores, normalmente se necesitan admitir las operaciones de deshacer, que los usuarios pueden invertir sus recientes cambios al modificar un elemento de código.  
  
 Mayoría de los diseñadores implementada en Visual Studio tiene compatibilidad de deshacer proporciona automáticamente el entorno.  
  
 Implementaciones de diseñador que necesitan para proporcionar compatibilidad con la característica de deshacer:  
  
-   Proporcione administración deshacer mediante la implementación de la clase base abstracta<xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>  
  
-   Admiten la persistencia de suministro y CodeDOM implementando la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>y la <xref:System.ComponentModel.Design.IComponentChangeService>clases.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Para obtener más información sobre cómo escribir diseñadores mediante [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], consulte [ampliar compatibilidad en tiempo de diseño](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona una infraestructura de deshacer de forma predeterminada por:  
  
-   Proporciona las implementaciones de administración a través de deshacer el <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>y <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>clases.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Proporciona persistencia y compatibilidad de CodeDOM a través de la opción predeterminada <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>y <xref:System.ComponentModel.Design.IComponentChangeService>implementaciones.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
## <a name="obtaining-undo-support-automatically"></a>Obtener soporte técnico de deshacer automáticamente  
 Cualquier creado en el diseñador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tiene deshacer automática y completa compatibilidad if, el diseñador:  
  
-   Hace uso de un <xref:System.Windows.Forms.Control>clase para la interfaz de usuario basada en.</xref:System.Windows.Forms.Control>  
  
-   Emplea el sistema de análisis y generación de código estándar basada en CodeDOM para la generación de código y la persistencia.  
  
     Para obtener más información sobre cómo trabajar con compatibilidad de CodeDOM de Visual Studio, consulte [compilación y generación de código fuente dinámico](http://msdn.microsoft.com/Library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Cuándo se debe utilizar la función de deshacer diseñador explícita  
 Diseñadores deben proporcionar su propia administración de deshacer si utilizan una interfaz gráfica de usuario, que se conoce como un adaptador de vista distinta de la proporcionada por <xref:System.Windows.Forms.Control>.</xref:System.Windows.Forms.Control>  
  
 Un ejemplo de esto podría crear un producto con una interfaz de diseño gráfico basada en web en lugar de un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] según la interfaz gráfica.  
  
 En tal caso, sería necesario registrar este adaptador de vista con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>y ofrecer una administración explícita deshacer.</xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>  
  
 Los diseñadores deben proporcionar compatibilidad con CodeDOM y persistencia si no utilizan el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de generación de código proporcionado en el <xref:System.CodeDom>espacio de nombres.</xref:System.CodeDom>  
  
## <a name="undo-support-features-of-the-designer"></a>Deshacer las características de compatibilidad del diseñador  
 El SDK de entorno proporciona implementaciones predeterminadas de las interfaces necesarias para proporcionar soporte técnico que puede utilizar los diseñadores no utiliza de deshacer <xref:System.Windows.Forms.Control>según las clases para sus interfaces de usuario o el modelo estándar de persistencia y CodeDOM.</xref:System.Windows.Forms.Control>  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>clase se deriva de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine>clase mediante la implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>clase para administrar las operaciones de deshacer.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> </xref:System.ComponentModel.Design.UndoEngine> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
 Visual Studio proporciona la siguiente función al diseñador de reversión:  
  
-   Funcionalidad de deshacer vinculada a través de varios diseñadores.  
  
-   Unidades secundarias dentro de un diseñador pueden interactuar con sus padres implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>  
  
 El SDK del entorno proporciona compatibilidad con CodeDOM y persistencia proporcionando:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>como una implementación de la<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
 Un <xref:System.ComponentModel.Design.IComponentChangeService>proporcionado por el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'' host de diseño.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Con las características SDK de entorno para proporcionar la función de deshacer  
 Para obtener soporte de deshacer, un objeto que implementa un diseñador debe:  
  
-   Crear instancias e inicializar una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>clase con válido <xref:System.IServiceProvider>implementación.</xref:System.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Esto <xref:System.IServiceProvider>clase debe proporcionar los siguientes servicios:</xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.</xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Diseñadores mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serialización de CodeDOM puede optar por usar <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>proporcionado con el [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] su implementación del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
         En este caso, la <xref:System.IServiceProvider>clase proporciona el <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>constructor debe devolver este objeto como una implementación de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>clase.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> </xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Diseñadores que utilicen el valor predeterminado <xref:System.ComponentModel.Design.DesignSurface>proporcionado por el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se garantiza que el host de diseño tiene una implementación predeterminada de la <xref:System.ComponentModel.Design.IComponentChangeService>clase</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.DesignSurface>  
  
 Los diseñadores que implementan un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>mecanismo de deshacer según automáticamente realiza un seguimiento de cambios si:</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Cambios de propiedad se realizan a través del <xref:System.ComponentModel.TypeDescriptor>objeto.</xref:System.ComponentModel.TypeDescriptor>  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>los eventos se generan manualmente cuando se confirma un cambio que se pueden deshacer.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
-   Modificaciones en el diseñador se ha creado en el contexto de un <xref:System.ComponentModel.Design.DesignerTransaction>.</xref:System.ComponentModel.Design.DesignerTransaction>  
  
-   El diseñador decide explícitamente crear unidades de deshacer mediante la unidad de deshacer estándar proporcionada por una implementación de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>o el Visual Studio específico de implementación <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>que se deriva de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>y también proporciona una implementación de ambos <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit>  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Ampliar la compatibilidad en tiempo de diseño](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
