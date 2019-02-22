---
title: Plantillas de elemento de proyecto de SharePoint y Project | Microsoft Docs
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3a535f1b9051835f0a26ae62ca63cc30f289ddea
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612925"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Proyecto de SharePoint y las plantillas de elemento de proyecto
  En las secciones siguientes se describen el proyecto de SharePoint y las plantillas de elemento de proyectos disponibles y cómo se utilizan.

## <a name="project-and-project-item-templates-overview"></a>Introducción a las plantillas de elemento de proyecto y de proyecto
 Cuando crea un nuevo proyecto de SharePoint en Visual Studio, se agrega un proyecto de SharePoint a la solución junto con todos los elementos de proyecto requeridos por ese tipo de proyecto. Por ejemplo, si crea un proyecto del elemento web de Silverlight, Visual Studio crea una solución que contiene un elemento de proyecto del elemento web visual y un elemento de proyecto de la aplicación de Silverlight, junto con todos los archivos necesarios para esos elementos de proyecto. Las plantillas de elementos de proyecto se utilizan para agregar elementos a un proyecto de SharePoint existente, por ejemplo, para agregar un receptor de eventos, una columna de sito o una lista.

 Para obtener información sobre los fundamentos de SharePoint, vea [bloques de creación de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404). Los usuarios avanzados pueden crear plantillas de proyecto y de elementos personalizadas de proyecto. Para obtener más información, consulte [extender el sistema de proyecto de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Plantillas de proyecto
 A continuación se ofrece una lista de las plantillas de proyecto de SharePoint. Para ver las plantillas de proyecto de SharePoint en Visual Studio, en el **nuevo proyecto** cuadro de diálogo, expanda el **SharePoint** nodo bajo **Visual C#** o  **Visual Basic**y, a continuación, elija **2010**.

### <a name="sharepoint-2010-project"></a>Proyecto de SharePoint 2010
 El contenido de un *proyecto de SharePoint 2010* se incluyen en cada plantilla de proyecto de SharePoint. Un Proyecto de SharePoint 2010 contiene:

-   Un archivo de proyecto.

-   Una página de propiedades del proyecto.

-   Un **referencias** carpeta enumerar todas las referencias de ensamblado en el proyecto.

-   Un **características** carpeta que contiene un *.feature* archivo de configuración, usado para implementar características en el servidor de SharePoint.

-   Un **paquete** carpeta que contiene un *Package.package* archivo, se usa para implementar la solución en SharePoint.

-   Un archivo key.snk (clave de nombre seguro) que se usa para firmar el ensamblado con un nombre seguro, para obtener una seguridad mejorada.

### <a name="sharepoint-2010-silverlight-web-part"></a>Elemento web de Silverlight de SharePoint 2010
 *Elemento Web de Silverlight de SharePoint 2010* proyectos le permiten crear elementos de web para SharePoint que muestran aplicaciones de Silverlight. Cuando cree este proyecto, podrá especificar si desea agregar una nueva aplicación de Silverlight al proyecto o hacer referencia a una ya existente. Para obtener más información, consulte [crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) y [Tutorial: Crear un elemento web de Silverlight que muestre OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Elemento web visual de SharePoint 2010
 Un *elemento Web de SharePoint 2010 Visual* proyecto incluye un *Elements.xml* archivo de definición, un **elemento Web** elemento y un **Control de usuario** elemento . Puede diseñar la apariencia del elemento web visual arrastrando o copiando los controles del cuadro de herramientas Visual Studio a la superficie del control de usuario. Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) y [bloques de creación: Elementos Web](http://go.microsoft.com/fwlink/?LinkId=179438).

### <a name="import-sharepoint-2010-solution-package"></a>Importar paquete de solución de SharePoint 2010
 *Importar paquete de solución de SharePoint 2010* proyectos permiten importar todo o parte de un sitio existente de SharePoint 2010, exportado a una solución de SharePoint (*.wsp*) archivo en Visual Studio. Una vez importado en Visual Studio, puede personalizar sus elementos e implementarlos de nuevo. Para obtener más información, consulte [importar elementos desde un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importar flujo de trabajo reutilizable de SharePoint 2010
 *Importar flujo de trabajo reutilizable SharePoint 2010* proyectos permiten importar un flujo de trabajo reutilizable y declarativo creado en SharePoint Designer 2010 en Visual Studio. El flujo de trabajo se exporta desde el sitio de SharePoint como un *.wsp* archivo. Una vez importado en Visual Studio, puede personalizarlo, agregarle código y, a continuación, implementarlo en un sitio de SharePoint. Para obtener más información, vea [Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Plantillas de elemento de proyecto
 A continuación se ofrece una lista de plantillas de elementos de proyecto de SharePoint. Las plantillas de elemento de proyecto agregan archivos a la solución de SharePoint para admitir la funcionalidad de SharePoint como columnas, listas y tipos de contenido de sitio. Por ejemplo, agregar una columna de sitio en la solución agrega un proyecto de columna de sitio que contiene un *Elements.xml* archivo de definición. Al agregar un elemento web visual, agrega un proyecto de elemento web visual a la solución que contiene un *Elements.xml* archivo, un elemento de control de usuario y un elemento web visual.

 Para ver las plantillas de elemento de proyecto de SharePoint, en **el Explorador de soluciones**, abra el menú contextual para un proyecto de SharePoint y, a continuación, elija **agregar**, **nuevo elemento**. Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija **2010**.

### <a name="application-page-farm-solution-only"></a>Página de aplicación (solución de granja de servidores únicamente)
 Un **página de aplicación (solución de granja de servidores únicamente)** elemento le permite diseñar un [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] página web para un sitio de SharePoint. Las páginas de aplicaciones solo se pueden utilizar en soluciones de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, vea [Cómo: Crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md) y [tipo de página de la aplicación _layouts](http://go.microsoft.com/fwlink/?LinkId=179434).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modelo de conectividad a datos empresariales (solución de granja de servidores únicamente)
 Un **(solución de granja de servidores únicamente) modelo de conectividad a datos empresariales** elemento le permite integrar los datos empresariales en SharePoint. Los datos profesionales pueden proceder de aplicaciones de servidor back-end, como [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel y SAP (Protocolo de anuncio de servicios). Los modelos de conectividad a datos profesionales solo se pueden utilizar en soluciones de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, vea [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md), [Cómo: Use un archivo de recursos para especificar nombres localizados, propiedades y permisos](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), y [cuáles son las novedades: Servicios de conectividad empresarial](http://go.microsoft.com/fwlink/?LinkId=179411).

### <a name="content-type"></a>Tipo de contenido
 *Tipo de contenido* elementos le permiten crear tipos de contenido personalizados en función de un tipo de contenido existente (base) como un documento, anuncio o una tarea. Un tipo de contenido personalizado proporciona los mismos atributos y campos que el tipo de contenido base junto con las columnas de sitio (capos) que se definan. Por ejemplo, puede crear un tipo de contenido personalizado Contacto basado en el tipo de contenido base Contacto que viene en SharePoint. Puede personalizar el tipo de contenido cambiando las columnas de sitio existentes o agregando más columnas de sitio a las que ya se incluyen en el tipo de contenido base.

> [!NOTE]
>  Debido a una limitación de SharePoint, no puede crear un tipo de contenido de solución de granja de servidores basado en un tipo de contenido de solución en espacio aislado.

 Para obtener más información, vea [Tutorial: Crear una columna de sitio, el tipo de contenido y la lista de SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) y [bloques de creación: Tipo de contenido](http://go.microsoft.com/fwlink/?LinkId=179413).

### <a name="empty-element"></a>Elemento vacío
 *Elementos vacíos* más a menudo se usan para definir los elementos de proyecto de SharePoint que carecen de un proyecto o una plantilla de elemento de proyecto en Visual Studio. Cuando se agrega un elemento vacío al proyecto, un nodo denominado EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] contiene un único archivo que es con nombre *Elements.xml.* Use [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrucciones para definir los elementos deseados en *Elements.xml*.

### <a name="event-receiver"></a>Receptor de eventos
 *Receptores de eventos* controlar los eventos de elementos en el sitio de SharePoint, como cuando se agrega un elemento a una lista, cuando se elimina un elemento web o cuando se inicia un flujo de trabajo. La plantilla del elemento de proyecto de receptor de eventos le permite controlar

- Eventos de lista

- Eventos de elementos de lista

- Eventos de correo electrónico de lista

- Eventos Web

- Eventos de flujo de trabajo de lista

  El elemento de proyecto de receptor de eventos crea un **receptor de eventos** carpeta con un archivo de clase único que contiene los controladores de eventos para todos los eventos que especificó cuando creó el proyecto en el **personalización de SharePoint Asistente para**. La clase del receptor de eventos puede controlar eventos que se producen en el sitio de SharePoint cuando se agrega, actualiza, elimina o quita elementos como archivos, campos, elementos, listas, datos adjuntos, elementos web y flujos de trabajo. Para obtener más información, vea [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md) y [bloques de creación: Control de eventos](http://go.microsoft.com/fwlink/?LinkId=179416).

### <a name="list"></a>Lista
 Una lista es una instancia de una definición de lista de base reutilizable de SharePoint, como un calendario o una lista de tareas. Después de agregar una lista a la solución, el Diseñador de listas permite agregar columnas de sitio a la lista y crear columnas de lista personalizada. Esto incluye columnas de sitio de tipos de contenido. Puede especificar el *vista* para la lista, que determina las columnas que aparecerán en la lista. Para obtener más información, vea [Tutorial: Crear una columna de sitio, el tipo de contenido y la lista de SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) y [bloques de creación: Las listas y bibliotecas de documentos](http://go.microsoft.com/fwlink/?LinkId=179421).

### <a name="module"></a>Module
 *Módulos* (para que no se debe confundir con [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos) contienen los archivos que desea implementar en el servidor de SharePoint, como imágenes o notas. El elemento de proyecto de módulo contiene un **módulo** nodo. El nodo módulo contiene dos plantillas de elemento de proyecto: un archivo de definición XML, que actúa como un manifiesto del módulo, y un *sample.txt* , un archivo de marcador de posición. Para obtener más información, consulte [utilizar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md) y [módulos](http://go.microsoft.com/fwlink/?LinkId=179425).

### <a name="sequential-workflow-farm-solution-only"></a>Flujo de trabajo secuencial (solución de granja de servidores únicamente)
 Un *flujo de trabajo secuencial* es una serie de pasos de lógica empresarial, se realizan en un orden hasta que se complete el último paso. Los flujos de trabajo secuenciales se utilizan para administrar procesos que implican elementos de SharePoint como listas y documentos. Puede crear flujos de trabajo de nivel de sitio (globales) o flujos de trabajo de nivel de lista (locales), así como seleccionar si un flujo de trabajo se inicia automática o manualmente. Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, consulte [soluciones de flujo de trabajo de SharePoint crear](../sharepoint/creating-sharepoint-workflow-solutions.md), [flujos de trabajo en SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), y [What ' s New: Mejoras de flujo de trabajo](http://go.microsoft.com/fwlink/?LinkId=179418).

### <a name="silverlight-web-part"></a>Elemento web de Silverlight
 *Elemento web de Silverlight* elementos de proyecto le permiten crear elementos de web para SharePoint que muestran aplicaciones de Silverlight. Cuando se agrega este elemento de proyecto a la solución, se puede optar por agregar una nueva aplicación de Silverlight o hacer referencia a una existente más adelante. Para obtener más información, consulte [crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) y [Tutorial: Crear un elemento web de Silverlight que muestre OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Columna de sitio
 Un *columna de sitio*, también conocida como un *campo*, es uno de los elementos más básicos que puede agregar a un proyecto de SharePoint. Una columna de sitio representa un tipo de datos, como un número de teléfono, un comentario de texto o el nombre de la ciudad de un contacto en una lista de contactos. Para obtener más información, consulte [crear listas, tipos de contenido y columnas de sitio para SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) y [columnas](http://go.microsoft.com/fwlink/?LinkId=226840).

### <a name="site-definition-farm-solution-only"></a>Definición de sitio (solución de granja de servidores únicamente)
 *Definición del sitio* elementos de proyecto contienen una carpeta de definición de sitio que incluye los siguientes archivos:

- Una página .aspx predeterminada, utilizada como página web predeterminada del sitio.

- Un *onet.xml* archivo que define los componentes del sitio.

- Un archivo webtemp xml especifica las configuraciones de definición de sitio que aparecen en la **selección de plantilla** sección de la **nuevo sitio de SharePoint** página.

  Después de agregar una definición de sitio, se agrega código y archivos que introducen la funcionalidad. Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, consulte [crear definiciones de sitios para SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) y [configuraciones y definiciones de sitio](http://go.microsoft.com/fwlink/?LinkId=260554).

### <a name="state-machine-workflow-farm-solution-only"></a>Flujo de trabajo de máquina de Estados (solución de granja de servidores únicamente)
 Un *flujo de trabajo de máquina de estados* es un conjunto de Estados de la lógica de negocios, transiciones y acciones. Los pasos de un flujo de trabajo de máquina de estados no se siguen en secuencia, sino que se activan mediante acciones y estados. Como un flujo de trabajo secuencial, los flujos de trabajo de máquina de estados están asociados a elementos de SharePoint como son las listas y los documentos. También en este caso puede crear flujos de trabajo de nivel de sitio (globales) o flujos de trabajo de nivel de lista (locales). Y también puede seleccionar si un flujo de trabajo se inicia automática o manualmente. Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, consulte [soluciones de flujo de trabajo de SharePoint crear](../sharepoint/creating-sharepoint-workflow-solutions.md), [flujos de trabajo en SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), y [What ' s New: Mejoras de flujo de trabajo](http://go.microsoft.com/fwlink/?LinkId=179418).

### <a name="user-control-farm-solution-only"></a>Control de usuario (solución de granja de servidores únicamente)
 Un *control de usuario* es un control personalizado y reutilizable al que puede agregar otros controles ASP.NET y controles de SharePoint. El control de usuario se puede agregar a las páginas de aplicación y elementos web que se ejecutan en SharePoint. Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, consulte [crear controles reutilizables para elementos Web o páginas de aplicación](http://go.microsoft.com/fwlink/?LinkId=226841).

### <a name="visual-web-part"></a>Elemento web Visual
 Un *elemento web visual* elemento de proyecto incluye un *Elements.xml* , archivo de definición de un **elemento Web** elemento y un **Control de usuario** elemento. Puede diseñar la apariencia del elemento web visual arrastrando o copiando los controles del cuadro de herramientas Visual Studio a la superficie del control de usuario. Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) y [bloques de creación: Elementos Web](http://go.microsoft.com/fwlink/?LinkId=179438).

### <a name="web-part"></a>Elemento web
 Un *elemento web* es un control de servidor que se ejecuta dentro de un tipo especial de página denominada una página de elementos Web. Hay bloques de compilación de las páginas que aparecen en un sitio de SharePoint. El elemento de elemento web proporciona archivos que permiten diseñar un elemento web para un sitio de SharePoint. Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) y [bloques de creación: Elementos Web](http://go.microsoft.com/fwlink/?LinkId=179438).

## <a name="see-also"></a>Vea también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Las tecnologías y productos de SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)
