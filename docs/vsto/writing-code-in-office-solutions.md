---
title: Escribir código en soluciones de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e9773c06293f189e572ef84e9b10f45a1ca5d5d8
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670993"
---
# <a name="write-code-in-office-solutions"></a>Escribir código en soluciones de Office
  Hay algunos aspectos de la escritura de código en proyectos de Office que difieren de otros tipos de proyectos de Visual Studio. Muchas de estas diferencias están relacionadas con la forma en que los modelos de objetos de Office se exponen al código administrado. Otras diferencias están relacionadas con el diseño de los proyectos de Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="managed-code-and-office-programming"></a>Código administrado y programación de Office  
 La tecnología clave que posibilita la creación de una solución integrada de Microsoft Office es Automation, que forma parte de la tecnología del Modelo de objetos componentes (COM). Automation permite utilizar código para crear y controlar los objetos de software que se exponen desde aplicaciones, DLL o controles ActiveX compatibles con las interfaces programáticas adecuadas.  
  
### <a name="understand-primary-interop-assemblies"></a>Comprender los ensamblados de interoperabilidad primarios  
 Las aplicaciones de Microsoft Office exponen gran parte de su funcionalidad a Automation. Sin embargo, no es posible utilizar código administrado (como Visual Basic o C#) directamente para automatizarlas. Para automatizar aplicaciones de Office mediante código administrado, debe utilizar los ensamblados de interoperabilidad primarios (PIA) de Office. Los ensamblados de interoperabilidad primarios permiten que el código administrado interactúe con el modelo de objetos basado en COM de las aplicaciones de Office.  
  
 Cada aplicación de Microsoft Office tiene un PIA. Al crear un proyecto de Office en Visual Studio, se agrega automáticamente al proyecto una referencia al PIA adecuado. Para automatizar las características de otras aplicaciones de Office desde el proyecto, debe agregar manualmente una referencia al PIA apropiado. Para obtener más información, consulte [Cómo: las aplicaciones de Office de destino a través de los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Usar ensamblados de interoperabilidad primarios en tiempo de ejecución y tiempo de diseño  
 Para realizar la mayoría de las tareas de desarrollo, debe tener los PIA de Office instalados y registrados en la caché global de ensamblados del equipo de desarrollo. Para obtener más información, consulte [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 Los PIA de Office no son obligatorios en los equipos de los usuarios finales para ejecutar soluciones de Office diseñadas para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Para obtener más información, consulte [diseño y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="use-types-in-primary-interop-assemblies"></a>Usar tipos en ensamblados de interoperabilidad primarios  
 Los PIA de Office contienen una combinación de tipos que expone el modelo de objetos de las aplicaciones de Office y tipos de infraestructura adicionales que no se han diseñado para utilizarse directamente en el código. Para obtener información general de los tipos de los PIA de Office, consulte [información general de las clases e interfaces de los ensamblados de interoperabilidad primarios de Office](/previous-versions/office/office-12/ms247299\(v\=office.12\)).  
  
 Puesto que los tipos de los PIA de Office se corresponden con los tipos de los modelos de objetos basados en COM, la manera de usar estos tipos suele diferir de la de otros tipos administrados. Por ejemplo, la forma de llamar a los métodos que tienen parámetros opcionales en un ensamblado de interoperabilidad primario de Office depende del lenguaje de programación que se utilice en el proyecto. Para obtener más información, consulta los temas siguientes:  
  
-   [Los parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md).  
  
-   [Enlace en tiempo de ejecución en soluciones de Office](../vsto/late-binding-in-office-solutions.md).  
  
## <a name="program-model-of-office-projects"></a>Modelo de sistema de proyectos de Office  
 Todos los proyectos de Office incluyen una o más clases generadas que proporcionan el punto de entrada para el código. Estas clases también proporcionan acceso al modelo de objetos de la aplicación host, y a características como los paneles de acciones y los paneles de tareas personalizados.  
  
### <a name="understand-the-generated-classes"></a>Comprender las clases generadas  
 En los proyectos de nivel de documento de Excel y Word, la clase generada es similar a un objeto de nivel superior en el modelo de objetos de la aplicación. Por ejemplo, la clase `ThisDocument` generada en un proyecto de documento de Word proporciona los mismos miembros que la clase <xref:Microsoft.Office.Interop.Word.Document> en el modelo de objetos de Word. Para obtener más información acerca de las clases generadas en proyectos de nivel de documento, consulte [programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
 Los proyectos de complementos de VSTO proporcionan una clase generada denominada `ThisAddIn`. Esta clase no se parece a una clase del modelo de objetos de la aplicación host. Por el contrario, esta clase representa al propio complemento de VSTO, y proporciona miembros que se pueden utilizar para tener acceso al modelo de objetos de la aplicación host y a otras características disponibles para los complementos de VSTO. Para obtener más información, consulte [complementos VSTO de programa](../vsto/programming-vsto-add-ins.md).  
  
 Todas las clases generadas de los proyectos de Office incluyen controladores de eventos `Startup` y `Shutdown`. Para empezar a escribir código, se suele agregar código a estos controladores de eventos. Para inicializar el complemento de VSTO, puede agregar código al controlador de eventos `Startup` . Para limpiar los recursos que usa el complemento de VSTO, puede agregar código al controlador de eventos `Shutdown`. Para obtener más información, consulte [eventos en proyectos de Office](../vsto/events-in-office-projects.md).  
  
### <a name="access-the-generated-classes-at-runtime"></a>Obtener acceso a las clases generadas en tiempo de ejecución  
 Cuando se carga una solución de Office, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea una instancia de cada una de las clases generadas del proyecto. Se puede tener acceso a estos objetos desde cualquier código del proyecto mediante la clase `Globals` . Por ejemplo, puede usar el `Globals` clase para llamar a código el `ThisAddIn` clase a partir de un controlador de eventos de un botón de la cinta de opciones en un complemento de VSTO.  
  
 Para obtener más información, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="namespace-considerations-in-office-solutions"></a>Consideraciones de Namespace en soluciones de Office  
 No se puede cambiar el *espacio de nombres predeterminado* (o el *espacio de nombres raíz* en Visual Basic) de un proyecto de Office después de crearlo. El espacio de nombres predeterminado siempre coincidirá con el nombre que se especifica para un proyecto cuando este se crea. Si cambia el nombre del proyecto, el espacio de nombres predeterminado no cambia. Para obtener más información sobre el espacio de nombres predeterminado en los proyectos, vea [Application Page, Project Designer &#40;C&#35; &#41; ](/visualstudio/ide/reference/application-page-project-designer-csharp) y [Application Page, Project Designer &#40;Visual Basic&#41; ](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Cambiar el espacio de nombres de clases de elementos host en proyectos de C#  
 Las clases de elementos host (por ejemplo, las clases `ThisAddIn`, `ThisWorkbook` o `ThisDocument`) tienen sus propios espacios de nombres en los proyectos de Office de Visual C#. De forma predeterminada, el espacio de nombres de los elementos host del proyecto coincide con el nombre que se especifica para un proyecto cuando este se crea.  
  
 Para cambiar el espacio de nombres de los elementos host de un proyecto de Office de Visual C#, utilice la propiedad **Espacio de nombres para el elemento host** . Para obtener más información, consulte [propiedades en proyectos de Office](../vsto/properties-in-office-projects.md).  
  
## <a name="supported-programming-languages-in-office-projects"></a>Lenguajes de programación admitidos en proyectos de Office  
 Las plantillas de proyecto de Office de Visual Studio solo admiten los lenguajes de programación Visual Basic y Visual C#. Por tanto, estas plantillas de proyecto solo están disponibles en los nodos **Visual Basic** y **Visual C#** del cuadro de diálogo **Nuevo proyecto** de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulte [Cómo: proyectos de creación de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="language-choice-and-office-programming"></a>Elección de lenguaje y programación de Office  
 Microsoft Office y Visual Basic para Aplicaciones (VBA) se desarrollaron para trabajar conjuntamente con el objetivo de optimizar el flujo de trabajo de personalización de las aplicaciones. Visual Basic ha heredado algunos de esos desarrollos. Por ejemplo, Visual Basic admite parámetros opcionales, lo que significa que puede escribir menos código al llamar a algunos métodos en los ensamblados de interoperabilidad primarios de Microsoft Office, que al utilizar Visual C#.  
  
## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Programa con vs de Visual Basic. Visual C# en soluciones de Office  
 Puede crear soluciones de Office mediante Visual Basic o Visual C#. Dado que los modelos de objetos de Microsoft Office se diseñaron para utilizarse con Microsoft Visual Basic para Aplicaciones (VBA), los desarrolladores de Visual Basic pueden trabajar cómodamente con los objetos que exponen las aplicaciones de Microsoft Office. Los desarrolladores de Visual C# pueden utilizar la mayoría de las características que los desarrolladores de Visual Basic, pero hay algunos casos en los que deben escribir código adicional para usar los modelos de objetos de Office. También hay algunas diferencias entre las características de programación básicas del desarrollo de Office y el código administrado que se escribe en Visual Basic y C#.  
  
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Diferencias principales entre Visual Basic y Visual C#  
 En la tabla siguiente se muestran las diferencias principales entre Visual Basic y Visual C# en el desarrollo de Office.  
  
|Característica|Descripción|Compatibilidad con Visual Basic|Compatibilidad con Visual C#|  
|-------------|-----------------|--------------------------|------------------------|  
|Parámetros opcionales|Muchos métodos de Microsoft Office tienen parámetros que no son necesarios cuando se les llama. Si no se pasa ningún valor para el parámetro, se utiliza un valor predeterminado.|Visual Basic admite parámetros opcionales.|Visual C# admite parámetros opcionales en la mayoría de los casos. Para obtener más información, consulte [parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Pasar parámetros por referencia|Los parámetros opcionales de la mayoría de los ensamblados de interoperabilidad primarios de Microsoft Office se pueden pasar por valor. Sin embargo, en algunos ensamblados de interoperabilidad primarios, los parámetros opcionales que aceptan tipos de referencia deben pasarse por referencia.<br /><br /> Para obtener más información acerca de los parámetros de tipo de valor y de referencia, consulte [pasar argumentos por valor y por referencia &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (para Visual Basic) y [pasar parámetros &#40;C&#35; Guía de programación&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|No es necesario realizar ningún trabajo adicional para pasar parámetros por referencia. El compilador de Visual Basic pasa automáticamente los parámetros por referencia cuando es necesario.|En la mayoría de los casos, el compilador de Visual C# pasa automáticamente los parámetros por referencia cuando es necesario. Para obtener más información, consulte [parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Propiedades parametrizadas|Algunas propiedades aceptan parámetros y actúan como funciones de solo lectura.|Visual Basic admite propiedades que aceptan parámetros.|Visual C# admite propiedades que aceptan parámetros.|  
|Enlace en tiempo de ejecución|El enlace en tiempo de ejecución implica determinar las propiedades de objetos en tiempo de ejecución, en lugar de convertir variables al tipo de objeto en tiempo de diseño.|Visual Basic realiza el enlace en tiempo de ejecución cuando **Option Strict** está desactivado. Cuando **Option Strict** está activado, debe convertir explícitamente los objetos y usar los tipos del espacio de nombres <xref:System.Reflection> para tener acceso a los miembros enlazados en tiempo de ejecución. Para obtener más información, consulte [enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md).|Visual C# realiza el enlace en tiempo de ejecución en proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Para obtener más información, consulte [enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md).|  
  
## <a name="key-differences-between-office-development-and-managed-code"></a>Diferencias clave entre el desarrollo de Office y el código administrado  
 En la tabla siguiente se muestran las diferencias principales entre el desarrollo para Office y el código administrado escrito en Visual Basic y Visual C#.  
  
|Característica|Descripción|Compatibilidad con Visual Basic y Visual C#|  
|-------------|-----------------|-----------------------------------------|  
|Índices de matriz|El límite de matriz inferior de las colecciones de aplicaciones de Microsoft Office comienza por 1. Visual Basic y Visual C# usan matrices basadas en 0. Para obtener más información, consulte [matrices &#40;C&#35; Guía de programación&#41; ](/dotnet/csharp/programming-guide/arrays/index) y [matrices en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Para obtener acceso al primer elemento de una colección en el modelo de objetos de una aplicación de Microsoft Office, utilice el índice 1 en lugar de 0.|  
  
## <a name="see-also"></a>Vea también  
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Eventos en proyectos de Office](../vsto/events-in-office-projects.md)   
 [Cómo: las aplicaciones de Office de destino a través de los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md)   
 [Desarrollo en colaboración de las soluciones de Office](../vsto/collaborative-development-of-office-solutions.md)  
  
  