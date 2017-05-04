---
title: "Plantillas de proyecto y de elementos de proyecto de SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.FirstWizardPage"
  - "VS.SharePointTools.SPE.ListInstance"
  - "VS.SharePointTools.SPE.ListDefinition"
  - "VS.SharePointTools.SPE.ListDefFromContentType"
  - "VS.SharePointTools.SPE.ContentType"
  - "SPE.Wizard"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, plantillas de proyecto y de elementos de proyecto"
  - "desarrollo de SharePoint en Visual Studio, plantillas"
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Plantillas de proyecto y de elementos de proyecto de SharePoint
  En las secciones siguientes se describen el proyecto de SharePoint y las plantillas de elemento de proyectos disponibles y cómo se utilizan.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="project_items_templates_overview"></a> Información general sobre plantillas de proyecto y de elementos de proyecto  
 Cuando se crea un nuevo proyecto de SharePoint en Visual Studio, se agrega un proyecto de SharePoint a la solución junto con todos los elementos del proyecto que requiere ese tipo de proyecto.  Por ejemplo, si crea un proyecto del elemento web de Silverlight, Visual Studio crea una solución que contiene un elemento de proyecto del elemento web visual y un elemento de proyecto de la aplicación de Silverlight, junto con todos los archivos necesarios para esos elementos de proyecto.  Las plantillas de elementos de proyecto se utilizan para agregar elementos a un proyecto de SharePoint existente, por ejemplo, para agregar un receptor de eventos, una columna de sito o una lista.  
  
 Para obtener información sobre los fundamentos de SharePoint, vea [Bloques de creación de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404).  Los usuarios avanzados pueden crear plantillas de proyecto y de elementos personalizadas de proyecto.  Para obtener más información, vea [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project_templates"></a> Plantillas de proyecto  
 A continuación se ofrece una lista de las plantillas de proyecto de SharePoint.  Para ver las plantillas de proyecto de SharePoint en Visual Studio, en el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **SharePoint** en **Visual C\#** o **Visual Basic** y, a continuación, elija **2010**.  
  
### Proyecto de SharePoint 2010  
 El contenido de un *Proyecto de SharePoint 2010* se incluye en cada plantilla de proyecto de SharePoint.  Un Proyecto de SharePoint 2010 contiene:  
  
-   Un archivo de proyecto.  
  
-   Una página de propiedades del proyecto.  
  
-   Una carpeta **Referencias** que enumera todas las referencias de ensamblado del proyecto.  
  
-   Una carpeta **Características** que contiene un archivo de configuración .feature, usado para implementar características en el servidor de SharePoint.  
  
-   Una carpeta **Paquete** que contiene un archivo Package.package, que se utiliza para implementar la solución en SharePoint.  
  
-   Un archivo key.snk \(clave de nombre seguro\) que se usa para firmar el ensamblado con un nombre seguro, para obtener una seguridad mejorada.  
  
### Elemento web de Silverlight de SharePoint 2010  
 Los proyectos *Elemento web de Silverlight de SharePoint 2010* permiten crear elementos web para SharePoint que muestran aplicaciones de Silverlight.  Cuando cree este proyecto, podrá especificar si desea agregar una nueva aplicación de Silverlight al proyecto o hacer referencia a una ya existente.  Para obtener más información, vea [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) y [Tutorial: Crear un elemento web de Silverlight que muestre OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### Elemento web visual de SharePoint 2010  
 Un proyecto *Elemento web visual de SharePoint 2010* incluye un archivo de definición Elements.xml, un elemento **Elemento web** y un elemento **Control de usuario**.  Puede diseñar el aspecto del elemento web visual arrastrando o copiando los controles del Cuadro de herramientas de Visual Studio a la superficie del control de usuario.  Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) y [Bloque de creación: elementos web](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### Importar paquete de solución de SharePoint 2010  
 Los proyectos *Importar paquete de solución de SharePoint 2010* permiten importar parte o la totalidad de un sitio de SharePoint existente 2010, exportado a un archivo de solución de SharePoint \(.wsp\), en Visual Studio.  Una vez importado en Visual Studio, puede personalizar sus elementos e implementarlos de nuevo.  Para obtener más información, vea [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### Importar el flujo de trabajo reutilizable de SharePoint 2010  
 Los proyectos *Importar el flujo de trabajo reutilizable de SharePoint 2010* permiten importar un flujo de trabajo reutilizable y declarativo creado en SharePoint Designer 2010 en Visual Studio.  El flujo de trabajo se exportó del sitio de SharePoint como un archivo .wsp.  Una vez importado en Visual Studio, puede personalizarlo, agregarle código y, a continuación, implementarlo en un sitio de SharePoint.  Para obtener más información, vea [Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project_item_templates"></a> Plantillas de elementos de proyecto  
 A continuación se ofrece una lista de plantillas de elementos de proyecto de SharePoint.  Las plantillas de elemento de proyecto agregan archivos a la solución de SharePoint para admitir la funcionalidad de SharePoint como columnas, listas y tipos de contenido de sitio.  Por ejemplo, al agregar una columna de sitio en la solución se agrega un proyecto de columna de sitio que contiene un archivo de definición Elements.xml.  Al agregar un elemento web visual se agrega un proyecto con un elemento web visual a la solución que contiene un archivo Elements.xml, un elemento de control de usuario y un elemento que contiene un elemento web visual.  
  
 Para ver las plantillas de elemento de proyecto de SharePoint, en el **Explorador de soluciones**, abra el menú contextual para un proyecto de SharePoint y, a continuación, elija **Agregar**, **Nuevo elemento**.  Expanda el nodo **SharePoint** bajo **Visual C\#** o **Visual Basic** y, a continuación, elija **2010**.  
  
### Página de aplicación \(solución de granja de servidores únicamente\)  
 Un elemento **Página de aplicación \(solución de granja de servidores únicamente\)** permite diseñar una página web [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] para un sitio de SharePoint.  Las páginas de aplicaciones solo se pueden utilizar en soluciones de granja de servidores.  Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores.  Para obtener más información, vea [Cómo: Crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md) y [Tipo de página de la aplicación \_layouts](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### Modelo de conectividad a datos profesionales \(solo en una solución de granja de servidores\)  
 Un elemento **Modelo de conectividad a datos profesionales \(solo en una solución de granja de servidores\)** permite integrar datos profesionales en SharePoint.  Los datos profesionales pueden proceder de aplicaciones de servidor back\-end, como [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel y SAP \(Protocolo de anuncio de servicios\).  Los modelos de conectividad a datos profesionales solo se pueden utilizar en soluciones de granja de servidores.  Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores.  Para obtener más información, vea [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md), [Cómo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), y [Novedades sobre los Servicios de conectividad empresarial](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### Tipo de contenido  
 Los elementos *tipo de contenido* permiten crear tipos de contenido personalizado basados en un tipo de contenido existente \(base\), como un documento, un anuncio o una tarea.  Un tipo de contenido personalizado proporciona los mismos atributos y campos que el tipo de contenido base junto con las columnas de sitio \(capos\) que se definan.  Por ejemplo, puede crear un tipo de contenido personalizado Contacto basado en el tipo de contenido base Contacto que viene en SharePoint.  Puede personalizar el tipo de contenido cambiando las columnas de sitio existentes o agregando más columnas de sitio a las que ya se incluyen en el tipo de contenido base.  
  
> [!NOTE]  
>  Debido a una limitación de SharePoint, no puede crear un tipo de contenido de solución de granja de servidores basado en un tipo de contenido de solución en espacio aislado.  
  
 Para obtener más información, vea [Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) y [Bloque de creación: tipos de contenido](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### Elemento vacío  
 Los *elementos vacíos* se usan normalmente para definir los elementos de proyecto de SharePoint que faltan una plantilla de proyecto o elemento de proyecto en Visual Studio.  Al agregar un elemento vacío al proyecto, se crea un nodo denominado EmptyElement\[x\]\(donde \[x\] es un número único\).  EmptyElement \[x\] contiene un archivo único que se denomina Elements.xml.  Utilice las instrucciones de [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] para definir los elementos que desee en Elements.xml.  
  
### Receptor de eventos  
 Los *receptores de eventos* controlan los eventos de los elementos del sitio de SharePoint, como cuando se agrega un elemento a una lista, cuando se elimina un elemento web o cuando se inicia un flujo de trabajo.  La plantilla del elemento de proyecto de receptor de eventos le permite controlar  
  
-   Eventos de lista  
  
-   Eventos de elementos de lista  
  
-   Eventos de correo electrónico de lista  
  
-   Eventos Web  
  
-   Eventos de flujo de trabajo de lista  
  
 El elemento de proyecto del receptor de eventos crea una carpeta **Receptor de eventos** con un archivo de clase único que contiene los controladores de eventos para todos los eventos que especificó cuando creó el proyecto en el **Asistente para personalización de SharePoint**.  La clase event receiver puede controlar los eventos que se producen en el sitio de SharePoint cuando se agregan, actualizan, eliminan o quitan elementos como archivos, campos, elementos, listas, datos adjuntos, elementos web y flujos de trabajo.  Para obtener más información, vea [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md) y [Bloque de creación: control de eventos](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### Lista  
 Una lista es una instancia de una definición de lista de base reutilizable de SharePoint, como un calendario o una lista de tareas.  Después de agregar una lista a la solución, el Diseñador de listas permite agregar columnas de sitio a la lista y crear columnas de lista personalizada.  Esto incluye columnas de sitio de tipos de contenido.  Puede especificar la *vista* de la lista, para determinar las columnas que aparecerán en la lista.  Para obtener más información, vea [Tutorial: Crear una lista, tipo de contenido y columna de sitio para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) y [Bloque de creación: bibliotecas de listas y documentos](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### Module  
 Los *módulos* \(que no se deben confundir con los módulos de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) contienen los archivos que se desean implementar al servidor de SharePoint, como imágenes o notas.  El elemento de proyecto de módulo contiene un nodo **Módulo**.  El nodo Módulo contiene dos plantillas de elementos de proyecto: un archivo de definición de XML, que actúa como manifiesto del módulo, y un archivo sample.txt, un archivo de marcador de posición.  Para obtener más información, vea [Utilizar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md) y [Módulos](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### Flujo de trabajo secuencial \(solución de granja de servidores únicamente\)  
 Un *flujo de trabajo secuencial* consiste en una serie de pasos de lógica empresarial que se lleva a cabo en secuencia hasta que se completa el último.  Los flujos de trabajo secuenciales se utilizan para administrar procesos que implican elementos de SharePoint como listas y documentos.  Puede crear flujos de trabajo de nivel de sitio \(globales\) o flujos de trabajo de nivel de lista \(locales\), así como seleccionar si un flujo de trabajo se inicia automática o manualmente.  Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores.  Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores.  Para obtener más información, vea [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [Flujos de trabajo en SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555) y [Novedades sobre las mejoras de los flujos de trabajo](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### Elemento web de Silverlight  
 Los elementos de proyecto *elemento web de Silverlight* permiten crear elementos web para SharePoint que muestran aplicaciones de Silverlight.  Cuando se agrega este elemento de proyecto a la solución, se puede optar por agregar una nueva aplicación de Silverlight o hacer referencia a una existente más adelante.  Para obtener más información, vea [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) y [Tutorial: Crear un elemento web de Silverlight que muestre OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### Columna de sitio  
 Una *columna de sitio*, también conocida como *campo*, es uno de los elementos más básicos que se pueden agregar a un proyecto de SharePoint.  Una columna de sitio representa un tipo de datos, como un número de teléfono, un comentario de texto o el nombre de la ciudad de un contacto en una lista de contactos.  Para obtener más información, vea [Crear listas, tipos de contenido y columnas de sitio para SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) y [Columnas](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### Definición de sitio \(solución de granja de servidores únicamente\)  
 Los elementos de proyecto *definición de sitio* contienen una carpeta de definición de sitio que incluye los siguientes archivos:  
  
-   Una página .aspx predeterminada, utilizada como página web predeterminada del sitio.  
  
-   Un archivo onet.xml, que define los componentes del sitio.  
  
-   Un archivo webtemp xml, que especifica las configuraciones de definición del sitio que aparecen en la sección **Selección de plantilla** de la página **Nuevo sitio de SharePoint**.  
  
 Después de agregar una definición de sitio, se agrega código y archivos que introducen la funcionalidad.  Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores.  Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores.  Para obtener más información, vea [Crear definiciones de sitio para SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) y [Configuraciones y definiciones de sitios](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### Flujo de trabajo de máquina de estados \(solución de granja de servidores únicamente\)  
 Un *flujo de trabajo de máquina de estados* es un conjunto de estados, transiciones y acciones de lógica empresarial.  Los pasos de un flujo de trabajo de máquina de estados no se siguen en secuencia, sino que se activan mediante acciones y estados.  Como un flujo de trabajo secuencial, los flujos de trabajo de máquina de estados están asociados a elementos de SharePoint como son las listas y los documentos.  También en este caso puede crear flujos de trabajo de nivel de sitio \(globales\) o flujos de trabajo de nivel de lista \(locales\).  Y también puede seleccionar si un flujo de trabajo se inicia automática o manualmente.  Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores.  Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores.  Para obtener más información, vea [Crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [Flujos de trabajo en SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555) y [Novedades sobre las mejoras de los flujos de trabajo](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### Control de usuario \(solución de granja de servidores únicamente\)  
 Un *control de usuario* es un control personalizado y reutilizable al que se pueden agregar otros controles ASP.NET y SharePoint.  El control de usuario se puede agregar a las páginas de aplicación y elementos web que se ejecutan en SharePoint.  Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores.  Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores.  Para obtener más información, vea cómo [crear controles reutilizables para elementos web o páginas de aplicación](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### Elemento web visual  
 Un elemento de proyecto *elemento web visual* incluye un archivo de definición Elements.xml, un elemento **Elemento web** y un elemento **Control de usuario**.  Puede diseñar el aspecto del elemento web visual arrastrando o copiando los controles del Cuadro de herramientas de Visual Studio a la superficie del control de usuario.  Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) y [Bloque de creación: elementos web](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### Elemento web  
 Un *elemento web* es un control de servidor que se ejecuta dentro de un tipo especial de página denominada una página de elementos web.  Hay bloques de compilación de las páginas que aparecen en un sitio de SharePoint.  El elemento de elemento web proporciona archivos que permiten diseñar un elemento web para un sitio de SharePoint.  Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) y [Bloque de creación: elementos web](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  