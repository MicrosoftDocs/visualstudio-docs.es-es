---
title: "Escribir c&#243;digo en soluciones de Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.RefactoringCancelled"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "soluciones [desarrollo de Office en Visual Studio], escribir código"
  - "código administrado [desarrollo de Office en Visual Studio]"
  - "desarrollo de Office en Visual Studio, lenguajes de programación compatibles"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], automatización"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], escribir código"
  - "escribir código para soluciones de Office"
  - "programación [desarrollo de Office en Visual Studio], modelo"
  - "Automatización [desarrollo de Office en Visual Studio], código administrado"
  - "desarrollo de aplicaciones [desarrollo de Office en Visual Studio], modelo de programación"
  - "Soluciones de Office [desarrollo de Office en Visual Studio], escribir código"
  - "automatizar aplicaciones de Office"
  - "desarrollo de aplicaciones [desarrollo de Office en Visual Studio], escribir código"
  - "desarrollo de aplicaciones [desarrollo de Office en Visual Studio], automatización"
  - "proyectos de Office [desarrollo de Office en Visual Studio], cambiar espacios de nombres"
  - "soluciones [desarrollo de Office en Visual Studio], modelo de programación"
  - "programación [desarrollo de Office en Visual Studio]"
  - "espacios de nombres [desarrollo de Office en Visual Studio], cambio en soluciones de Office"
  - "proyectos [desarrollo de Office en Visual Studio], escribir código"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], modelo de programación"
  - "extensiones de código administrado [desarrollo de Office en Visual Studio], escribir código"
ms.assetid: 2d4d8fd0-e881-4829-976f-0d1a9221dec0
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Escribir c&#243;digo en soluciones de Office
  Hay algunos aspectos de la escritura de código en proyectos de Office que difieren de otros tipos de proyectos de Visual Studio. Muchas de estas diferencias están relacionadas con la forma en que los modelos de objetos de Office se exponen al código administrado. Otras diferencias están relacionadas con el diseño de los proyectos de Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Código administrado y programación en Office  
 La tecnología clave que posibilita la creación de una solución integrada de Microsoft Office es la automatización, que forma parte de la tecnología del Modelo de objetos componentes \(COM\). La automatización permite utilizar código para crear y controlar los objetos de software que se exponen desde aplicaciones, DLL o controles ActiveX compatibles con las interfaces programáticas adecuadas.  
  
### Introducción a los ensamblados de interoperabilidad primarios  
 Las aplicaciones de Microsoft Office exponen gran parte de su funcionalidad a la automatización. Sin embargo, no es posible utilizar código administrado \(como Visual Basic o C\#\) directamente para automatizarlas. Para automatizar aplicaciones de Office mediante código administrado, debe utilizar los ensamblados de interoperabilidad primarios \(PIA\) de Office. Los ensamblados de interoperabilidad primarios permiten que el código administrado interactúe con el modelo de objetos basado en COM de las aplicaciones de Office.  
  
 Cada aplicación de Microsoft Office tiene un PIA. Al crear un proyecto de Office en Visual Studio, se agrega automáticamente al proyecto una referencia al PIA adecuado. Para automatizar las características de otras aplicaciones de Office desde el proyecto, debe agregar manualmente una referencia al PIA apropiado. Para obtener más información, consulta [Cómo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
### Usar ensamblados de interoperabilidad primarios en tiempo de diseño y en tiempo de ejecución  
 Para realizar la mayoría de las tareas de desarrollo, debe tener los PIA de Office instalados y registrados en la caché global de ensamblados del equipo de desarrollo. Para obtener más información, consulta [Configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 Los PIA de Office no son obligatorios en los equipos de los usuarios finales para ejecutar soluciones de Office diseñadas para [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores. Para obtener más información, consulta [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).  
  
### Usar tipos en ensamblados de interoperabilidad primarios  
 Los PIA de Office contienen una combinación de tipos que expone el modelo de objetos de las aplicaciones de Office y tipos de infraestructura adicionales que no se han diseñado para utilizarse directamente en el código. Para obtener información general de los tipos de los PIA de Office, vea [Overview of Classes and Interfaces in the Office Primary Interop Assemblies](http://msdn.microsoft.com/es-es/da92dc3c-8209-44de-8095-a843659368d5).  
  
 Puesto que los tipos de los PIA de Office se corresponden con los tipos de los modelos de objetos basados en COM, la manera de usar estos tipos suele diferir de la de otros tipos administrados. Por ejemplo, la forma de llamar a los métodos que tienen parámetros opcionales en un ensamblado de interoperabilidad primario de Office depende del lenguaje de programación que se utilice en el proyecto. Para obtener más información, consulta los temas siguientes:  
  
-   [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md).  
  
-   [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md).  
  
## Modelo de programación de proyectos de Office  
 Todos los proyectos de Office incluyen una o más clases generadas que proporcionan el punto de entrada para el código. Estas clases también proporcionan acceso al modelo de objetos de la aplicación host, y a características como los paneles de acciones y los paneles de tareas personalizados.  
  
### Introducción a las clases generadas  
 En los proyectos de nivel de documento de Excel y Word, la clase generada es similar a un objeto de nivel superior en el modelo de objetos de la aplicación. Por ejemplo, la clase `ThisDocument` generada en un proyecto de documento de Word proporciona los mismos miembros que la clase <xref:Microsoft.Office.Interop.Word.Document> en el modelo de objetos de Word. Para obtener más información acerca de las clases generadas en proyectos de nivel de documento, vea [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
 Los proyectos de complementos de VSTO proporcionan una clase generada denominada `ThisAddIn`. Esta clase no se parece a una clase del modelo de objetos de la aplicación host. Por el contrario, esta clase representa al propio complemento de VSTO, y proporciona miembros que se pueden utilizar para tener acceso al modelo de objetos de la aplicación host y a otras características disponibles para los complementos de VSTO. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Todas las clases generadas de los proyectos de Office incluyen controladores de eventos `Startup` y `Shutdown`. Para empezar a escribir código, se suele agregar código a estos controladores de eventos. Para inicializar el complemento de VSTO, puede agregar código al controlador de eventos `Startup`. Para limpiar los recursos que usa el complemento de VSTO, puede agregar código al controlador de eventos `Shutdown`. Para obtener más información, consulta [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md).  
  
### Obtener acceso a las clases generadas en tiempo de ejecución  
 Cuando se carga una solución de Office, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crea una instancia de cada una de las clases generadas del proyecto. Se puede tener acceso a estos objetos desde cualquier código del proyecto mediante la clase `Globals`. Por ejemplo, puede utilizar la clase `Globals` para llamar a código en la clase `ThisAddIn`, desde un controlador de eventos de un botón de la cinta de opciones de un complemento de VSTO.  
  
 Para obtener más información, consulta [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### Consideraciones sobre los espacios de nombres en soluciones de Office  
 No se puede cambiar el *espacio de nombres predeterminado* \(o el *espacio de nombres raíz* en Visual Basic\) de un proyecto de Office después de crearlo. El espacio de nombres predeterminado siempre coincidirá con el nombre que se especifica para un proyecto cuando este se crea. Si cambia el nombre del proyecto, el espacio de nombres predeterminado no cambia. Para obtener más información sobre el espacio de nombres predeterminado en los proyectos, vea [Página de aplicación, Diseñador de proyectos &#40;C&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) y [Aplicación &#40;Página, Diseñador de proyectos&#41; &#40;Visual Basic&#41;](../ide/reference/application-page-project-designer-visual-basic.md).  
  
### Cambiar el espacio de nombres de clases de elementos host en proyectos de C\#  
 Las clases de elementos host \(por ejemplo, las clases `ThisAddIn`, `ThisWorkbook` o `ThisDocument`\) tienen sus propios espacios de nombres en los proyectos de Office de Visual C\#. De forma predeterminada, el espacio de nombres de los elementos host del proyecto coincide con el nombre que se especifica para un proyecto cuando este se crea.  
  
 Para cambiar el espacio de nombres de los elementos host de un proyecto de Office de Visual C\#, utilice la propiedad **Espacio de nombres para el elemento host**. Para obtener más información, consulta [Propiedades de los proyectos de Office](../vsto/properties-in-office-projects.md).  
  
## Lenguajes de programación admitidos en proyectos de Office  
 Las plantillas de proyecto de Office de Visual Studio solo admiten los lenguajes de programación Visual Basic y Visual C\#. Por tanto, estas plantillas de proyecto solo están disponibles en los nodos **Visual Basic** y **Visual C\#** del cuadro de diálogo **Nuevo proyecto** de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulta [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Elección de lenguaje y programación en Office  
 Microsoft Office y Visual Basic para Aplicaciones \(VBA\) se desarrollaron para trabajar conjuntamente con el objetivo de optimizar el flujo de trabajo de personalización de las aplicaciones. Visual Basic ha heredado algunos de esos desarrollos. Por ejemplo, Visual Basic admite parámetros opcionales, lo que significa que puede escribir menos código al llamar a algunos métodos en los ensamblados de interoperabilidad primarios de Microsoft Office, que al utilizar Visual C\#.  
  
## Programación con Visual Basic frente a Visual C\# en las soluciones de Office  
 Puede crear soluciones de Office mediante Visual Basic o Visual C\#. Dado que los modelos de objetos de Microsoft Office se diseñaron para utilizarse con Microsoft Visual Basic para Aplicaciones \(VBA\), los desarrolladores de Visual Basic pueden trabajar cómodamente con los objetos que exponen las aplicaciones de Microsoft Office. Los desarrolladores de Visual C\# pueden utilizar la mayoría de las características que los desarrolladores de Visual Basic, pero hay algunos casos en los que deben escribir código adicional para usar los modelos de objetos de Office. También hay algunas diferencias entre las características de programación básicas del desarrollo de Office y el código administrado que se escribe en Visual Basic y C\#.  
  
## Diferencias principales entre Visual Basic y Visual C\#  
 En la tabla siguiente se muestran las diferencias principales entre Visual Basic y Visual C\# en el desarrollo de Office.  
  
|Característica|Descripción|Compatibilidad con Visual Basic|Compatibilidad con Visual C\#|  
|--------------------|-----------------|-------------------------------------|-----------------------------------|  
|Parámetros opcionales|Muchos métodos de Microsoft Office tienen parámetros que no son necesarios cuando se les llama. Si no se pasa ningún valor para el parámetro, se utiliza un valor predeterminado.|Visual Basic admite parámetros opcionales.|Visual C\# admite parámetros opcionales en la mayoría de los casos. Para obtener más información, consulta [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Pasar parámetros por referencia|Los parámetros opcionales de la mayoría de los ensamblados de interoperabilidad primarios de Microsoft Office se pueden pasar por valor. Sin embargo, en algunos ensamblados de interoperabilidad primarios, los parámetros opcionales que aceptan tipos de referencia deben pasarse por referencia.<br /><br /> Para obtener más información sobre los parámetros de tipo de valor y de referencia, vea [Pasar argumentos por valor y por referencia &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) \(para Visual Basic\) y [Pasar parámetros &#40;Guía de programación de C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|No es necesario realizar ningún trabajo adicional para pasar parámetros por referencia. El compilador de Visual Basic pasa automáticamente los parámetros por referencia cuando es necesario.|En la mayoría de los casos, el compilador de Visual C\# pasa automáticamente los parámetros por referencia cuando es necesario. Para obtener más información, consulta [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Propiedades parametrizadas|Algunas propiedades aceptan parámetros y actúan como funciones de solo lectura.|Visual Basic admite propiedades que aceptan parámetros.|Visual C\# admite propiedades que aceptan parámetros.|  
|Enlace en tiempo de ejecución|El enlace en tiempo de ejecución implica determinar las propiedades de objetos en tiempo de ejecución, en lugar de convertir variables al tipo de objeto en tiempo de diseño.|Visual Basic realiza el enlace en tiempo de ejecución cuando **Option Strict**  está desactivado. Cuando **Option Strict** está activado, debe convertir explícitamente los objetos y usar los tipos del espacio de nombres <xref:System.Reflection> para tener acceso a los miembros enlazados en tiempo de ejecución. Para obtener más información, consulta [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md).|Visual C\# realiza el enlace en tiempo de ejecución en proyectos que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Para obtener más información, consulta [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md).|  
  
## Diferencias principales entre el desarrollo para Office y el código administrado  
 En la tabla siguiente se muestran las diferencias principales entre el desarrollo para Office y el código administrado escrito en Visual Basic y Visual C\#.  
  
|Característica|Descripción|Compatibilidad con Visual Basic y Visual C\#|  
|--------------------|-----------------|--------------------------------------------------|  
|Índices de matriz|El límite de matriz inferior de las colecciones de aplicaciones de Microsoft Office comienza por 1. Visual Basic y Visual C\# usan matrices basadas en 0. Para obtener más información, vea [Matrices &#40;Guía de programación de C&#35;&#41;](/dotnet/csharp/programming-guide/arrays/index) y [Matrices en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Para obtener acceso al primer elemento de una colección en el modelo de objetos de una aplicación de Microsoft Office, utilice el índice 1 en lugar de 0.|  
  
## Vea también  
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md)   
 [Cómo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md)   
 [Desarrollo en colaboración de las soluciones de Office](../vsto/collaborative-development-of-office-solutions.md)  
  
  