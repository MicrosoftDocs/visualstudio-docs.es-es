---
title: Personalización de características de la interfaz de usuario mediante interfaces de extensibilidad
description: Obtenga información sobre que las herramientas de desarrollo de Office Visual Studio proporcionan interfaces de extensibilidad que le ayudan a personalizar las características de la interfaz de usuario.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 86f4e5f286d817fb3f657e40399eccd3a2b4de73
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828038"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Personalización de características de la interfaz de usuario mediante interfaces de extensibilidad
  Las herramientas de desarrollo de Office en Visual Studio proporcionan clases y diseñadores que administran numerosos detalles de la implementación cuando se usan para crear paneles de tareas personalizados, personalizaciones de la cinta y regiones de formularios de Outlook en un complemento VSTO. Sin embargo, también puede implementar la *interfaz de extensibilidad* para cada característica si tiene necesidades especiales.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Introducción a las interfaces de extensibilidad
 Microsoft Office define un conjunto de interfaces de extensibilidad que los complementos COM VSTO pueden implementar para personalizar determinadas características, como la cinta. Estas interfaces proporcionan un control completo sobre las características a las que proporcionan acceso. Sin embargo, para implementar estas interfaces se necesitan conocimientos sobre la interoperabilidad de COM en código administrado. En algunos casos, el modelo de programación de estas interfaces tampoco resulta intuitivo para los desarrolladores que están acostumbrados a .NET Framework.

 Cuando se crea un complemento VSTO mediante las plantillas de proyecto de Office en Visual Studio, no es necesario implementar las interfaces de extensibilidad para personalizar características como la cinta. El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] implementa estas interfaces automáticamente. En su lugar, puede usar las clases y los diseñadores más intuitivos que Visual Studio proporciona. Sin embargo, puede implementar las interfaces de extensibilidad directamente en su complemento VSTO si lo desea.

 Para obtener más información sobre las clases y diseñadores que Visual Studio proporciona [](../vsto/ribbon-designer.md)para estas características, vea Paneles de tareas [personalizados,](../vsto/custom-task-panes.md)Diseñador de cinta de opciones y Crear regiones de formulario [de Outlook.](../vsto/creating-outlook-form-regions.md)

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Interfaces de extensibilidad que puede implementar en un complemento de VSTO
 La tabla siguiente enumera las interfaces de extensibilidad que puede implementar, y las aplicaciones que las admiten.

|Interfaz|Descripción|APLICACIONES|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implemente esta interfaz para personalizar la interfaz de usuario de la cinta. **Nota:**  Puede agregar un elemento **de cinta de opciones (XML)** a un proyecto para generar una implementación predeterminada en el complemento de <xref:Microsoft.Office.Core.IRibbonExtensibility> VSTO. Para obtener más información, consulta [Ribbon XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implemente esta interfaz para crear un panel de tareas personalizado.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implemente esta interfaz para crear una región de formulario de Outlook.|Outlook|

 Hay algunas otras interfaces de extensibilidad definidas por Microsoft Office, como <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>y <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio no permite implementar estas interfaces en un complemento VSTO creado mediante plantillas de proyectos de Office.

## <a name="use-extensibility-interfaces"></a>Uso de interfaces de extensibilidad
 Para personalizar una característica de interfaz de usuario , mediante una interfaz de extensibilidad, implemente la interfaz apropiada en su proyecto de complemento VSTO. Después, invalide el método <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> para que devuelva una instancia de la clase que implementa la interfaz.

 Para obtener una aplicación de ejemplo que muestra cómo implementar las interfaces , y en un complemento <xref:Microsoft.Office.Core.IRibbonExtensibility> <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> de <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> VSTO para Outlook, [](../vsto/office-development-samples.md)vea el ejemplo de UI Manager en ejemplos de desarrollo de Office .

### <a name="example-of-implementing-an-extensibility-interface"></a>Ejemplo de implementación de una interfaz de extensibilidad
 El ejemplo de código siguiente muestra una implementación simple de la interfaz <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> para crear un panel de tareas personalizado. Este ejemplo define dos clases:

- La clase `TaskPaneHelper` implementa <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> para crear y mostrar un panel de tareas personalizado.

- La clase `TaskPaneUI` proporciona la interfaz de usuario del panel de tareas. Los atributos de la clase `TaskPaneUI` hacen que la clase sea visible para COM, lo que permite que las aplicaciones de Microsoft Office detecten la clase. En este ejemplo, la interfaz de usuario es un <xref:System.Windows.Forms.UserControl>vacío, pero puede agregar controles modificando el código.

  > [!NOTE]
  > Para exponer la clase `TaskPaneUI` a COM, también debe establecer la propiedad **Registrar para interoperabilidad COM** para el proyecto.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet1":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet1":::

  Para obtener más información sobre cómo implementar , vea Crear paneles de tareas personalizados en el sistema <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> [de Office 2007](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) en la Microsoft Office personalizada.

### <a name="example-of-overriding-the-requestservice-method"></a>Ejemplo de reemplazo del método RequestService
 El siguiente código de ejemplo muestra cómo invalidar el método <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> para devolver una instancia de la clase `TaskPaneHelper` del ejemplo de código anterior. Comprueba el valor del parámetro *serviceGuid* para determinar qué interfaz se está solicitando, y devuelve un objeto que implementa esa interfaz.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs" id="Snippet2":::

## <a name="see-also"></a>Consulte también
- [Ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Programación de complementos VSTO](../vsto/programming-vsto-add-ins.md)
- [Desarrollo de soluciones de Office](../vsto/developing-office-solutions.md)
- [Llamada de código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
