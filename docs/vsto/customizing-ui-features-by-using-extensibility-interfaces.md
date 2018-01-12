---
title: "Personalizar características de interfaz de usuario mediante Interfaces de extensibilidad | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 404b54ea189c00b26f43a39274dfaf44ef37773a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="customizing-ui-features-by-using-extensibility-interfaces"></a>Personalizar características de la interfaz de usuario mediante interfaces de extensibilidad
  Las herramientas de desarrollo de Office en Visual Studio proporcionan clases y diseñadores que administran numerosos detalles de la implementación cuando se usan para crear paneles de tareas personalizados, personalizaciones de la cinta y regiones de formularios de Outlook en un complemento VSTO. Sin embargo, también puede implementar la *interfaz de extensibilidad* para cada característica si tiene necesidades especiales.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="overview-of-extensibility-interfaces"></a>Introducción a las interfaces de extensibilidad  
 Microsoft Office define un conjunto de interfaces de extensibilidad que los complementos COM VSTO pueden implementar para personalizar determinadas características, como la cinta. Estas interfaces proporcionan un control completo sobre las características a las que proporcionan acceso. Sin embargo, para implementar estas interfaces se necesitan conocimientos sobre la interoperabilidad de COM en código administrado. En algunos casos, el modelo de programación de estas interfaces tampoco resulta intuitivo para los desarrolladores que están acostumbrados a .NET Framework.  
  
 Cuando se crea un complemento VSTO mediante las plantillas de proyecto de Office en Visual Studio, no es necesario implementar las interfaces de extensibilidad para personalizar características como la cinta. El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] implementa estas interfaces automáticamente. En su lugar, puede usar las clases y los diseñadores más intuitivos que Visual Studio proporciona. Sin embargo, puede implementar las interfaces de extensibilidad directamente en su complemento VSTO si lo desea.  
  
 Para obtener más información acerca de las clases y los diseñadores que Visual Studio proporciona para estas características, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md), [Diseñador de la cinta](../vsto/ribbon-designer.md), y [crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).  
  
## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Interfaces de extensibilidad que puede implementar en un complemento VSTO  
 La tabla siguiente enumera las interfaces de extensibilidad que puede implementar, y las aplicaciones que las admiten.  
  
|Interfaz|Descripción|Aplicaciones|  
|---------------|-----------------|------------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implemente esta interfaz para personalizar la interfaz de usuario de la cinta. **Nota:** puede agregar un **cinta (XML)** elemento a un proyecto para generar el valor predeterminado es <xref:Microsoft.Office.Core.IRibbonExtensibility> implementación en el complemento de VSTO. Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proyecto<br /><br /> Visio<br /><br /> Palabra|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implemente esta interfaz para crear un panel de tareas personalizado.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Palabra|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implemente esta interfaz para crear una región de formulario de Outlook.|Outlook|  
  
 Hay algunas otras interfaces de extensibilidad definidas por Microsoft Office, como <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>y <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio no permite implementar estas interfaces en un complemento VSTO creado mediante plantillas de proyectos de Office.  
  
## <a name="using-extensibility-interfaces"></a>Usar interfaces de extensibilidad  
 Para personalizar una característica de interfaz de usuario , mediante una interfaz de extensibilidad, implemente la interfaz apropiada en su proyecto de complemento VSTO. Después, invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> para que devuelva una instancia de la clase que implementa la interfaz.  
  
 Para ver un ejemplo de aplicación que muestre cómo puede implementar las interfaces <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>y <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> en un complemento VSTO para Outlook, consulte el ejemplo del administrador de interfaz de usuario en [Office Development Samples](../vsto/office-development-samples.md).  
  
### <a name="example-of-implementing-an-extensibility-interface"></a>Ejemplo de implementación de una interfaz de extensibilidad  
 El ejemplo de código siguiente muestra una implementación simple de la interfaz <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> para crear un panel de tareas personalizado. Este ejemplo define dos clases:  
  
-   La clase `TaskPaneHelper` implementa <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> para crear y mostrar un panel de tareas personalizado.  
  
-   La clase `TaskPaneUI` proporciona la interfaz de usuario del panel de tareas. Los atributos de la clase `TaskPaneUI` hacen que la clase sea visible para COM, lo que permite que las aplicaciones de Microsoft Office detecten la clase. En este ejemplo, la interfaz de usuario es un <xref:System.Windows.Forms.UserControl>vacío, pero puede agregar controles modificando el código.  
  
    > [!NOTE]  
    >  Para exponer la clase `TaskPaneUI` a COM, también debe establecer la propiedad **Registrar para interoperabilidad COM** para el proyecto.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]  
  
 Para obtener más información sobre cómo implementar <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, vea [Crear paneles de tareas personalizados en 2007 Office System](http://msdn.microsoft.com/en-us/256313db-18cc-496c-a961-381ed9ca94be) , en la documentación de Microsoft Office.  
  
### <a name="example-of-overriding-the-requestservice-method"></a>Ejemplo de invalidación del método RequestService  
 El siguiente código de ejemplo muestra cómo invalidar el método <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> para devolver una instancia de la clase `TaskPaneHelper` del ejemplo de código anterior. Comprueba el valor del parámetro *serviceGuid* para determinar qué interfaz se está solicitando, y devuelve un objeto que implementa esa interfaz.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Llamar a código en complementos VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
  