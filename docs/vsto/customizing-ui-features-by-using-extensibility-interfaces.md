---
title: "Personalizar caracter&#237;sticas de la interfaz de usuario mediante interfaces de extensibilidad"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ICustomTaskPaneConsumer (interfaz)"
  - "IRibbonExtensibility (interfaz)"
  - "personalizar la interfaz de usuario [desarrollo de Office en Visual Studio]"
  - "interfaces de usuario [desarrollo de Office en Visual Studio], personalizar"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], interfaces de extensibilidad"
  - "personalizar características de la interfaz de usuario [desarrollo de Office en Visual Studio]"
  - "FormRegionStartup (interfaz)"
  - "complementos [desarrollo de Office en Visual Studio], interfaces de extensibilidad"
  - "interfaces de extensibilidad [desarrollo de Office en Visual Studio]"
ms.assetid: 3f3f7908-9404-4eda-8899-4d18c75e3b4a
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Personalizar caracter&#237;sticas de la interfaz de usuario mediante interfaces de extensibilidad
  Las herramientas de desarrollo de Office en Visual Studio proporcionan clases y diseñadores que administran numerosos detalles de la implementación cuando se usan para crear paneles de tareas personalizados, personalizaciones de la cinta y regiones de formularios de Outlook en un complemento VSTO. Sin embargo, también puede implementar la *interfaz de extensibilidad* para cada característica si tiene necesidades especiales.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Introducción a las interfaces de extensibilidad  
 Microsoft Office define un conjunto de interfaces de extensibilidad que los complementos COM VSTO pueden implementar para personalizar determinadas características, como la cinta. Estas interfaces proporcionan un control completo sobre las características a las que proporcionan acceso. Sin embargo, para implementar estas interfaces se necesitan conocimientos sobre la interoperabilidad de COM en código administrado. En algunos casos, el modelo de programación de estas interfaces tampoco resulta intuitivo para los desarrolladores que están acostumbrados a .NET Framework.  
  
 Cuando se crea un complemento VSTO mediante las plantillas de proyecto de Office en Visual Studio, no es necesario implementar las interfaces de extensibilidad para personalizar características como la cinta. El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] implementa estas interfaces automáticamente. En su lugar, puede usar las clases y los diseñadores más intuitivos que Visual Studio proporciona. Sin embargo, puede implementar las interfaces de extensibilidad directamente en su complemento VSTO si lo desea.  
  
 Para obtener más información sobre las clases y los diseñadores que Visual Studio proporciona para estas características, consulte [Paneles de tareas personalizados](../vsto/custom-task-panes.md), [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md) y [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).  
  
## Interfaces de extensibilidad que puede implementar en un complemento VSTO  
 La tabla siguiente enumera las interfaces de extensibilidad que puede implementar, y las aplicaciones que las admiten.  
  
|Interfaz|Descripción|Aplicaciones|  
|--------------|-----------------|------------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implemente esta interfaz para personalizar la interfaz de usuario de la cinta. **Note:**  Puede agregar un elemento **Cinta \(XML\)** al proyecto para generar una implementación <xref:Microsoft.Office.Core.IRibbonExtensibility> predeterminada en su complemento VSTO. Para obtener más información, consulta [XML de la cinta de opciones](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proyecto<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implemente esta interfaz para crear un panel de tareas personalizado.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implemente esta interfaz para crear una región de formulario de Outlook.|Outlook|  
  
 Hay algunas otras interfaces de extensibilidad definidas por Microsoft Office, como <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider> y <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio no permite implementar estas interfaces en un complemento VSTO creado mediante plantillas de proyectos de Office.  
  
## Usar interfaces de extensibilidad  
 Para personalizar una característica de interfaz de usuario , mediante una interfaz de extensibilidad, implemente la interfaz apropiada en su proyecto de complemento VSTO. Después, invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> para que devuelva una instancia de la clase que implementa la interfaz.  
  
 Para ver un ejemplo de aplicación que muestre cómo puede implementar las interfaces <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> y <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> en un complemento VSTO para Outlook, consulte el ejemplo del administrador de interfaz de usuario en [Ejemplos de desarrollo de Office](../vsto/office-development-samples.md).  
  
### Ejemplo de implementación de una interfaz de extensibilidad  
 El ejemplo de código siguiente muestra una implementación simple de la interfaz <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> para crear un panel de tareas personalizado. Este ejemplo define dos clases:  
  
-   La clase `TaskPaneHelper` implementa <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> para crear y mostrar un panel de tareas personalizado.  
  
-   La clase `TaskPaneUI` proporciona la interfaz de usuario del panel de tareas. Los atributos de la clase `TaskPaneUI` hacen que la clase sea visible para COM, lo que permite que las aplicaciones de Microsoft Office detecten la clase. En este ejemplo, la interfaz de usuario es un <xref:System.Windows.Forms.UserControl> vacío, pero puede agregar controles modificando el código.  
  
    > [!NOTE]  
    >  Para exponer la clase `TaskPaneUI` a COM, también debe establecer la propiedad **Registrar para interoperabilidad COM** para el proyecto.  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_SimpleExtensibilityInterface#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#1)]  
  
 Para obtener más información sobre cómo implementar <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, vea [Crear paneles de tareas personalizados en 2007 Office System](http://msdn.microsoft.com/es-es/256313db-18cc-496c-a961-381ed9ca94be), en la documentación de Microsoft Office.  
  
### Ejemplo de invalidación del método RequestService  
 El siguiente código de ejemplo muestra cómo invalidar el método <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> para devolver una instancia de la clase `TaskPaneHelper` del ejemplo de código anterior. Comprueba el valor del parámetro *serviceGuid* para determinar qué interfaz se está solicitando, y devuelve un objeto que implementa esa interfaz.  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#2)]  
  
## Vea también  
 [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Llamar a código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
  