---
title: Proporcionar compatibilidad con la deshacer para diseñadores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675340"
---
# <a name="supplying-undo-support-to-designers"></a>Compatibilidad de la característica Deshacer en los diseñadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los diseñadores, como los editores, normalmente necesitan admitir las operaciones de deshacer para que los usuarios puedan invertir sus cambios recientes al modificar un elemento de código.  
  
 La mayoría de los diseñadores implementados en Visual Studio tienen soporte de deshacer automáticamente proporcionado por el entorno.  
  
 Implementaciones de diseñador que necesitan proporcionar compatibilidad con la característica de deshacer:  
  
- Proporcionar administración de deshacer mediante la implementación de la clase base abstracta <xref:System.ComponentModel.Design.UndoEngine>  
  
- Proporcione persistencia y compatibilidad con CodeDOM implementando las <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> clases y.  
  
  Para obtener más información sobre cómo escribir diseñadores mediante [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , vea [extender la compatibilidad en tiempo de diseño](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Proporciona una infraestructura de deshacer predeterminada mediante:  
  
- Proporcionar implementaciones de administración de deshacer a través de las <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> clases y.  
  
- Proporcionar persistencia y compatibilidad con CodeDOM a través de las implementaciones predeterminadas <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> de y <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
## <a name="obtaining-undo-support-automatically"></a>Obtener soporte técnico para deshacer automáticamente  
 Cualquier diseñador creado en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tiene compatibilidad de deshacer automática y completa si, el diseñador:  
  
- Hace uso de una <xref:System.Windows.Forms.Control> clase basada en para su interfaz de usuario.  
  
- Emplea el sistema de análisis y generación de código basado en CodeDOM estándar para la generación y persistencia de código.  
  
     Para obtener más información sobre cómo trabajar con la compatibilidad de CodeDOM de Visual Studio, vea [generación y compilación de código fuente dinámico](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb) .  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Cuándo usar la compatibilidad con la deshacer explícita del diseñador  
 Los diseñadores deben proporcionar su propia administración de deshacer si utilizan una interfaz de usuario gráfica, que se conoce como adaptador de vista, aparte de la proporcionada por <xref:System.Windows.Forms.Control> .  
  
 Un ejemplo de esto podría ser la creación de un producto con una interfaz de diseño gráfico basada en Web en lugar de una [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] interfaz gráfica basada en.  
  
 En tales casos, es necesario registrar este adaptador de vista con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mediante y <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> proporcionar administración de deshacer explícita.  
  
 Los diseñadores deben proporcionar compatibilidad con CodeDOM y persistencia si no usan el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelo de generación de código proporcionado en el <xref:System.CodeDom> espacio de nombres.  
  
## <a name="undo-support-features-of-the-designer"></a>Características de soporte para deshacer del diseñador  
 El SDK de entorno proporciona implementaciones predeterminadas de las interfaces necesarias para proporcionar compatibilidad con la deshacer que pueden usar los diseñadores que no usan <xref:System.Windows.Forms.Control> clases basadas en sus interfaces de usuario o el modelo CodeDom y de persistencia estándar.  
  
 La <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase se deriva de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> clase utilizando una implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> clase para administrar las operaciones de deshacer.  
  
 Visual Studio proporciona la siguiente característica para deshacer el diseñador:  
  
- Funcionalidad de deshacer vinculada en varios diseñadores.  
  
- Las unidades secundarias dentro de un diseñador pueden interactuar con sus elementos primarios implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> en <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  El SDK de entorno proporciona compatibilidad con CodeDOM y persistencia proporcionando:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> como implementaciones del <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  <xref:System.ComponentModel.Design.IComponentChangeService>Proporcionado por el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] host de diseño ' '.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Uso de las características del SDK de entorno para proporcionar compatibilidad con la deshacer  
 Para obtener soporte para deshacer, un objeto que implementa un diseñador debe:  
  
- Cree instancias e inicialice una instancia de la <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> clase con una <xref:System.IServiceProvider> implementación válida.  
  
- Esta <xref:System.IServiceProvider> clase debe proporcionar los siguientes servicios:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Los diseñadores [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que usan la serialización CodeDom pueden optar por usar <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> proporcionados con [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] como su implementación de <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       En este caso, la <xref:System.IServiceProvider> clase proporcionada al <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> constructor debe devolver este objeto como una implementación de la <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> clase.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Se garantiza que los diseñadores que usan el valor predeterminado <xref:System.ComponentModel.Design.DesignSurface> proporcionado por el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] host de diseño tienen una implementación predeterminada de la <xref:System.ComponentModel.Design.IComponentChangeService> clase.  
  
  Los diseñadores que implementan un <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mecanismo de deshacer basado en realizan automáticamente un seguimiento de los cambios si  
  
- Los cambios en las propiedades se realizan a través del <xref:System.ComponentModel.TypeDescriptor> objeto.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> los eventos se generan manualmente cuando se confirma un cambio que se pueden deshacer.  
  
- La modificación en el diseñador se creó en el contexto de un <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- El diseñador elige crear explícitamente las unidades de deshacer mediante la unidad de deshacer estándar que proporciona una implementación de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> o la implementación específica de Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , que deriva de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> y también proporciona una implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> y <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>Consulte también  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Ampliar la compatibilidad en tiempo de diseño](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
