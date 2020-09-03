---
title: Plantillas de proyecto y de elemento de proyecto de SharePoint | Microsoft Docs
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
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649222"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Plantillas de proyecto y de elemento de proyecto de SharePoint
  En las secciones siguientes se describen el proyecto de SharePoint y las plantillas de elemento de proyectos disponibles y cómo se utilizan.

## <a name="project-and-project-item-templates-overview"></a>Introducción a las plantillas de proyecto y elemento de proyecto
 Cuando se crea un nuevo proyecto de SharePoint en Visual Studio, se agrega un proyecto de SharePoint a la solución junto con todos los elementos del proyecto que requiere ese tipo de proyecto. Por ejemplo, si crea un proyecto del elemento web de Silverlight, Visual Studio crea una solución que contiene un elemento de proyecto del elemento web visual y un elemento de proyecto de la aplicación de Silverlight, junto con todos los archivos necesarios para esos elementos de proyecto. Las plantillas de elementos de proyecto se utilizan para agregar elementos a un proyecto de SharePoint existente, por ejemplo, para agregar un receptor de eventos, una columna de sito o una lista.

 Para obtener información sobre los aspectos básicos de SharePoint, vea [bloques de creación de SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Los usuarios avanzados pueden crear plantillas de proyecto y de elementos personalizadas de proyecto. Para obtener más información, vea [extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Plantillas de proyecto
 A continuación se ofrece una lista de las plantillas de proyecto de SharePoint. Para ver las plantillas de proyecto de SharePoint en Visual Studio, en el cuadro de diálogo **nuevo proyecto** , expanda el nodo **SharePoint** en **Visual C#** o en **Visual Basic**y, a continuación, elija **2010**.

### <a name="sharepoint-2010-project"></a>Proyecto de SharePoint 2010
 El contenido de un *proyecto de sharepoint 2010* se incluye en todas las plantillas de proyecto de SharePoint. Un Proyecto de SharePoint 2010 contiene:

- Un archivo de proyecto.

- Una página de propiedades del proyecto.

- Una carpeta de **referencias** que enumera todas las referencias de ensamblado del proyecto.

- Carpeta de **características** que contiene un archivo *de configuración de características,* que se usa para implementar características en el servidor de SharePoint.

- Una carpeta de **paquetes** que contiene un archivo *Package. Package* , que se usa para implementar la solución en SharePoint.

- Un archivo key.snk (clave de nombre seguro) que se usa para firmar el ensamblado con un nombre seguro, para obtener una seguridad mejorada.

### <a name="sharepoint-2010-silverlight-web-part"></a>Elemento Web de Silverlight de SharePoint 2010
 Los proyectos de *elementos Web de Silverlight de sharepoint 2010* permiten crear elementos Web para SharePoint que muestran aplicaciones de Silverlight. Cuando cree este proyecto, podrá especificar si desea agregar una nueva aplicación de Silverlight al proyecto o hacer referencia a una ya existente. Para obtener más información, vea [crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) y [Tutorial: crear un elemento Web de Silverlight que muestre OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Elemento Web visual de SharePoint 2010
 Un proyecto de *elemento Web visual de SharePoint 2010* incluye un archivo de definición de *Elements.xml* , un elemento de **elemento Web** y un elemento de **control de usuario** . Puede diseñar el aspecto del elemento web visual arrastrando o copiando los controles del Cuadro de herramientas de Visual Studio a la superficie del control de usuario. Para obtener más información, vea [Cómo: crear un elemento Web de SharePoint mediante un diseñador y un](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [bloque de creación: elementos Web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Importar paquete de solución de SharePoint 2010
 *Importar proyectos de paquetes de solución de sharepoint 2010* le permite importar todo o parte de un sitio de SharePoint 2010 existente, exportado a un archivo de solución de SharePoint (*. wsp*) en Visual Studio. Una vez importado en Visual Studio, puede personalizar sus elementos e implementarlos de nuevo. Para obtener más información, vea [importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importar flujo de trabajo de SharePoint 2010 reutilizable
 *Importar proyectos de flujo de trabajo de sharepoint 2010 reutilizables* le permiten importar un flujo de trabajo declarable y reutilizable creado en SharePoint Designer 2010 en Visual Studio. El flujo de trabajo se exporta desde el sitio de SharePoint como un archivo *. wsp* . Una vez importado en Visual Studio, puede personalizarlo, agregarle código y, a continuación, implementarlo en un sitio de SharePoint. Para obtener más información, vea [Tutorial: importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Plantillas de elementos de proyecto
 A continuación se ofrece una lista de plantillas de elementos de proyecto de SharePoint. Las plantillas de elemento de proyecto agregan archivos a la solución de SharePoint para admitir la funcionalidad de SharePoint como columnas, listas y tipos de contenido de sitio. Por ejemplo, al agregar una columna de sitio a la solución, se agrega un proyecto de columna de sitio que contiene un archivo de definición de *Elements.xml* . Al agregar un elemento Web visual, se agrega un proyecto de elemento Web visual a la solución que contiene un archivo de *Elements.xml* , un elemento de control de usuario y un elemento de elemento Web visual.

 Para ver las plantillas de elementos de proyecto de SharePoint, en **Explorador de soluciones**, abra el menú contextual de un proyecto de SharePoint y, a continuación, elija **Agregar**, **nuevo elemento**. Expanda el nodo **SharePoint** en **Visual C#** o **Visual Basic**y, a continuación, elija **2010**.

### <a name="application-page-farm-solution-only"></a>Página de aplicación (solución de granja de servidores únicamente)
 Un elemento **Página de aplicación (solo solución de granja de servidores)** permite diseñar una [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Página Web para un sitio de SharePoint. Las páginas de aplicaciones solo se pueden utilizar en soluciones de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, consulte [Cómo: crear una página de aplicación y un](../sharepoint/how-to-create-an-application-page.md) tipo de [Página _layouts de aplicación](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Modelo de conectividad a datos profesionales (solo solución de granja de servidores)
 Un elemento **modelo de conectividad a datos profesionales (solo solución de granja de servidores)** permite integrar datos empresariales en SharePoint. Los datos profesionales pueden proceder de aplicaciones de servidor back-end, como [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel y SAP (Protocolo de anuncio de servicios). Los modelos de conectividad a datos profesionales solo se pueden utilizar en soluciones de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, vea [Cómo: crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md), [Cómo usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), y [novedades: servicios de conectividad empresarial](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Tipo de contenido
 Los elementos de *tipo de contenido* permiten crear tipos de contenido personalizados basados en un tipo de contenido existente (base) como un documento, un anuncio o una tarea. Un tipo de contenido personalizado proporciona los mismos atributos y campos que el tipo de contenido base junto con las columnas de sitio (capos) que se definan. Por ejemplo, puede crear un tipo de contenido personalizado Contacto basado en el tipo de contenido base Contacto que viene en SharePoint. Puede personalizar el tipo de contenido cambiando las columnas de sitio existentes o agregando más columnas de sitio a las que ya se incluyen en el tipo de contenido base.

> [!NOTE]
> Debido a una limitación de SharePoint, no puede crear un tipo de contenido de solución de granja de servidores basado en un tipo de contenido de solución en espacio aislado.

 Para obtener más información, consulte [Tutorial: crear una columna de sitio, tipo de contenido y lista para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) y [bloque de creación: tipo de contenido](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Elemento vacío
 *Los elementos vacíos* se suelen usar para definir elementos de proyecto de SharePoint que carecen de una plantilla de proyecto o de elemento de proyecto en Visual Studio. Al agregar un elemento vacío al proyecto, se crea un nodo denominado EmptyElement [x] (donde [x] es un número único \) . EmptyElement [x] contiene un único archivo denominado *Elements.xml.* Use [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrucciones para definir los elementos deseados en *Elements.xml*.

### <a name="event-receiver"></a>Receptor de eventos
 Los *receptores de eventos* controlan los eventos de los elementos del sitio de SharePoint, por ejemplo, cuando se agrega un elemento a una lista, cuando se elimina un elemento Web o cuando se inicia un flujo de trabajo. La plantilla del elemento de proyecto de receptor de eventos le permite controlar

- Enumera los eventos.

- Eventos de elementos de lista

- Eventos de correo electrónico de lista

- Eventos Web

- Eventos de flujo de trabajo de lista

  El elemento de proyecto del receptor de eventos crea una carpeta de **receptor de eventos** con un solo archivo de clase que contiene controladores de eventos para todos los eventos que se especificaron al crear el proyecto en el **Asistente para la personalización de SharePoint**. La clase de receptor de eventos puede controlar los eventos que se producen en el sitio de SharePoint cuando se agregan, actualizan, eliminan o quitan elementos como archivos, campos, elementos, listas, datos adjuntos, elementos Web y flujos de trabajo. Para obtener más información, vea [Cómo: crear un receptor de eventos y un](../sharepoint/how-to-create-an-event-receiver.md) bloque de [creación: control de eventos](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>Lista
 Una lista es una instancia de una definición de lista de base reutilizable de SharePoint, como un calendario o una lista de tareas. Después de agregar una lista a la solución, el Diseñador de listas permite agregar columnas de sitio a la lista y crear columnas de lista personalizada. Esto incluye columnas de sitio de tipos de contenido. Puede especificar la *vista* de la lista, que determina las columnas que aparecerán en la lista. Para obtener más información, consulte [Tutorial: crear una columna de sitio, tipo de contenido y lista para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) y [bloque de creación: listas y bibliotecas de documentos](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Módulo
 Los *módulos* (que no se deben confundir con los [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos) contienen los archivos que desea implementar en el servidor de SharePoint, como imágenes o notas. El elemento de proyecto de módulo contiene un nodo de **módulo** . El nodo módulo contiene dos plantillas de elementos de proyecto: un archivo de definición XML, que actúa como manifiesto para el módulo y un archivo de *sample.txt* , un archivo de marcador de posición. Para obtener más información, vea [usar módulos para incluir archivos en la solución y en los](../sharepoint/using-modules-to-include-files-in-the-solution.md) [módulos](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Flujo de trabajo secuencial (solo solución de granja de servidores)
 Un *flujo de trabajo secuencial* es una serie de pasos de lógica de negocios, que se realizan en secuencia, hasta que se completa el último paso. Los flujos de trabajo secuenciales se utilizan para administrar procesos que implican elementos de SharePoint como listas y documentos. Puede crear flujos de trabajo de nivel de sitio (globales) o flujos de trabajo de nivel de lista (locales), así como seleccionar si un flujo de trabajo se inicia automática o manualmente. Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, vea [crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flujos de trabajo en SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))y [novedades: mejoras en el flujo de trabajo](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Elemento Web de Silverlight
 Los elementos de proyecto de *elementos Web de Silverlight* permiten crear elementos Web para SharePoint que muestran aplicaciones de Silverlight. Cuando se agrega este elemento de proyecto a la solución, se puede optar por agregar una nueva aplicación de Silverlight o hacer referencia a una existente más adelante. Para obtener más información, vea [crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) y [Tutorial: crear un elemento Web de Silverlight que muestre OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Columna de sitio
 Una *columna de sitio*, también conocida como *campo*, es uno de los elementos más básicos que se pueden agregar a un proyecto de SharePoint. Una columna de sitio representa un tipo de datos, como un número de teléfono, un comentario de texto o el nombre de la ciudad de un contacto en una lista de contactos. Para obtener más información, vea [crear columnas de sitio, tipos de contenido y listas para SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) y [columnas](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definición de sitio (solo solución de granja de servidores)
 Los elementos de proyecto de *definición de sitio* contienen una carpeta de definición de sitio que incluye los siguientes archivos:

- Una página .aspx predeterminada, utilizada como página web predeterminada del sitio.

- Un archivo *onet.xml* que define los componentes del sitio.

- Un archivo XML de WebTemp que especifica las configuraciones de definición de sitio que aparecen en la sección **selección de plantilla** de la página **nuevo sitio de SharePoint** .

  Después de agregar una definición de sitio, se agrega código y archivos que introducen la funcionalidad. Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, vea [crear definiciones de sitio para SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) y [definiciones y configuraciones de sitios](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Flujo de trabajo de equipo de estado (solo solución de granja de servidores)
 Un *flujo de trabajo de equipo de estado* es un conjunto de Estados, transiciones y acciones de lógica de negocios. Los pasos de un flujo de trabajo de máquina de estados no se siguen en secuencia, sino que se activan mediante acciones y estados. Como un flujo de trabajo secuencial, los flujos de trabajo de máquina de estados están asociados a elementos de SharePoint como son las listas y los documentos. También en este caso puede crear flujos de trabajo de nivel de sitio (globales) o flujos de trabajo de nivel de lista (locales). Y también puede seleccionar si un flujo de trabajo se inicia automática o manualmente. Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, vea [crear soluciones de flujo de trabajo de SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [flujos de trabajo en SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))y [novedades: mejoras en el flujo de trabajo](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Control de usuario (solo solución de granja de servidores)
 Un *control de usuario* es un control personalizado y reutilizable al que se pueden agregar otros controles ASP.net y controles de SharePoint. El control de usuario se puede agregar a las páginas de aplicación y elementos web que se ejecutan en SharePoint. Este elemento de proyecto únicamente se puede usar en una solución de granja de servidores. Puede agregar este elemento de proyecto únicamente a las soluciones de granja de servidores. Para obtener más información, vea [crear controles reutilizables para elementos Web o páginas de aplicación](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Elemento Web Visual
 Un elemento de proyecto de *elemento Web visual* incluye un archivo de definición de *Elements.xml* , un elemento de **elemento Web** y un elemento de **control de usuario** . Puede diseñar el aspecto del elemento web visual arrastrando o copiando los controles del Cuadro de herramientas de Visual Studio a la superficie del control de usuario. Para obtener más información, vea [Cómo: crear un elemento Web de SharePoint mediante un diseñador y un](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) [bloque de creación: elementos Web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Elemento web
 Un *elemento Web* es un control del lado servidor que se ejecuta dentro de un tipo especial de página denominada página de elementos Web. Hay bloques de compilación de las páginas que aparecen en un sitio de SharePoint. El elemento de elemento web proporciona archivos que permiten diseñar un elemento web para un sitio de SharePoint. Para obtener más información, vea [Cómo: crear un elemento Web de SharePoint y un](../sharepoint/how-to-create-a-sharepoint-web-part.md) bloque de [creación: elementos Web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Vea también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Productos y Tecnologías de SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
