---
title: Proporcionar deshacer a diseñadores | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ca68d0046e7dc46087fa6de3835bd6246bc58e1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267363"
---
# <a name="supplying-undo-support-to-designers"></a>Compatibilidad de la característica Deshacer en los diseñadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Normalmente los diseñadores, editores, al igual que deben admitir las operaciones de deshacer para que los usuarios pueden invertir sus recientes cambios al modificar un elemento de código.  
  
 Mayoría de los diseñadores implementada en Visual Studio tiene soporte para deshacer automáticamente proporcionada por el entorno.  
  
 Implementaciones de diseñador que necesitan para proporcionar compatibilidad con la característica de reversión:  
  
-   Proporcionar deshacer la administración mediante la implementación de la clase base abstracta <xref:System.ComponentModel.Design.UndoEngine>  
  
-   Admiten la persistencia de suministro y CodeDOM al implementar el <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> y <xref:System.ComponentModel.Design.IComponentChangeService> clases.  
  
 Para obtener más información sobre cómo escribir los diseñadores que utilizan [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], consulte [ampliar compatibilidad en tiempo de diseño](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 El [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] proporciona una infraestructura de deshacer de forma predeterminada por:  
  
-   Proporcionar las implementaciones de administración a través de deshacer la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> y <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> clases.  
  
-   Proporciona persistencia y la compatibilidad de CodeDOM a través de la predeterminada <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> y <xref:System.ComponentModel.Design.IComponentChangeService> implementaciones.  
  
## <a name="obtaining-undo-support-automatically"></a>Obtener soporte para deshacer automáticamente  
 Cualquier creado en el diseñador [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] es compatible con la fase de reversión automática y completa if, el diseñador:  
  
-   Hace uso de un <xref:System.Windows.Forms.Control> en función de clase para la interfaz de usuario.  
  
-   Emplea el sistema de análisis y generación de código estándar basado en CodeDOM para la persistencia y la generación de código.  
  
     Para obtener más información sobre cómo trabajar con la compatibilidad de CodeDOM de Visual Studio, consulte [generación de código fuente dinámico y la compilación](http://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Cuándo usar Deshacer diseñador explícita  
 Los diseñadores deben proporcionar su propia administración de deshacer si usan una interfaz gráfica de usuario que se conoce como un adaptador de vista, distinta de la proporcionada por <xref:System.Windows.Forms.Control>.  
  
 Un ejemplo de esto podría crear un producto con una interfaz de diseño gráfica basada en web en lugar de un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] en función de la interfaz gráfica.  
  
 En tales casos, sería necesario registrar este adaptador de vista con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mediante <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>y proporciona la administración de la fase de reversión explícita.  
  
 Los diseñadores deben proporcionar CodeDOM y persistencia de soporte técnico si no usan el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporcionado en el modelo de generación de código la <xref:System.CodeDom> espacio de nombres.  
  
## <a name="undo-support-features-of-the-designer"></a>Compatibilidad con características del Diseñador de deshacer  
 El SDK del entorno proporciona implementaciones predeterminadas de las interfaces necesarias para proporcionar soporte técnico que se puede utilizar los diseñadores que no utilizan de deshacer <xref:System.Windows.Forms.Control> en función de las clases para sus interfaces de usuario o el modelo de persistencia y CodeDOM estándar.  
  
 El <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase se deriva de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> clase mediante la implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> clase para administrar las operaciones de deshacer.  
  
 Visual Studio proporciona la siguiente funcionalidad para deshacer diseñador:  
  
-   Funcionalidad de deshacer vinculada entre varios diseñadores.  
  
-   Unidades secundarias dentro de un diseñador pueden interactuar con sus elementos primarios mediante la implementación <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> en <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 El SDK del entorno proporciona compatibilidad con CodeDOM y persistencia proporcionando:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> como un implementaciones de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Un <xref:System.ComponentModel.Design.IComponentChangeService> proporcionada por el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'' host de diseño.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Uso de las características del SDK de entorno para proporcionar soporte para deshacer  
 Para obtener soporte para deshacer, un objeto que implementa un diseñador debe:  
  
-   Crear una instancia e inicializar una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase con válido <xref:System.IServiceProvider> implementación.  
  
-   Esto <xref:System.IServiceProvider> clase debe proporcionar los siguientes servicios:  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Los diseñadores que utilizan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] serialización de CodeDOM se puede optar por usar <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> proporcionado con el [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] como su implementación de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         En este caso, el <xref:System.IServiceProvider> clase proporcionada para el <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> constructor debe devolver este objeto como una implementación de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> clase.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Los diseñadores que utilizan el valor predeterminado <xref:System.ComponentModel.Design.DesignSurface> proporcionada por el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] host de diseño se garantiza que tiene una implementación predeterminada de la <xref:System.ComponentModel.Design.IComponentChangeService> clase.  
  
 Los diseñadores que implementan un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mecanismo en función de deshacer automáticamente realiza un seguimiento de cambios si:  
  
-   Los cambios de propiedad se realizan a través del <xref:System.ComponentModel.TypeDescriptor> objeto.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService> los eventos se generan manualmente cuando se confirma un cambio que se puede deshacer.  
  
-   Modificación en el diseñador se creó en el contexto de un <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   El diseñador decide crear explícitamente mediante cualquiera de unidades de deshacer de la unidad de deshacer estándar proporcionada por una implementación de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> o la implementación específica de Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, que se deriva de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> y también proporciona un implementación de ambos <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Ampliar compatibilidad en tiempo de diseño](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)

