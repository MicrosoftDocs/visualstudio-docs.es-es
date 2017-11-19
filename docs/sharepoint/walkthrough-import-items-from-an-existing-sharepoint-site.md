---
title: 'Tutorial: Importar elementos de un sitio de SharePoint existente | Documentos de Microsoft'
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 602615426a8aeca118f6faba65e21778136b0ce6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Tutorial: Importar elementos de un sitio de SharePoint
  Este tutorial muestra cómo importar elementos de un sitio de SharePoint existente en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Personalizar un sitio de SharePoint mediante la adición de una columna de sitio personalizada (también conocido como un *campo*.  
  
-   Exportar un sitio de SharePoint a un archivo .wsp.  
  
-   Importar el archivo .wsp en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint usando el proyecto de importación wsp.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="customizing-a-sharepoint-site"></a>Personalizar un sitio de SharePoint  
 En este ejemplo, se cree y personalice un subsitio de SharePoint mediante la adición de una nueva columna de sitio a él y creando otro subsitio para su uso posterior. Posteriormente, se exportará el primero subsitio a un archivo .wsp y, a continuación, importar la columna de sitio personalizada en el segundo subsitio utilizando el proyecto de importación wsp.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Para crear y personalizar un sitio de SharePoint  
  
1.  Abrir un sitio de SharePoint mediante un explorador Web, como http://*nombre del sistema*  /SitePages/Home.aspx.  
  
2.  Cree un subsitio fuera del sitio de SharePoint principal abriendo el **acciones del sitio** menú y, a continuación, eligiendo **nuevo sitio**.  
  
3.  En el sitio **crear** diálogo cuadro, elija la **en blanco sitio** tipo.  
  
4.  En el **título** cuadro, escriba **prueba 1 de la columna de sitio**; en el **nombre de dirección URL** cuadro, escriba **columntest1**; deje los otros valores en su valor predeterminado valores; y, a continuación, elija la **crear** botón.  
  
5.  Una vez creado el sitio, navegue en el explorador al sitio principal, http://*nombre del sistema*  /SitePages/Home.aspx.  
  
6.  Nuevo, cree un subsitio en blanco fuera del sitio de SharePoint principal abriendo el **acciones del sitio** menú, elegir **nuevo sitio**y, a continuación, elija la **en blanco sitio** tipo.  
  
7.  En el **título** cuadro, escriba **columna sitio prueba 2**; en el **nombre de dirección URL** cuadro, escriba **columntest2**; deje los otros valores en su valor predeterminado valores; y, a continuación, elija la **crear** botón.  
  
8.  Vuelva a la primera subsitio, http://*SystemName*/columntest1/default.aspx.  
  
9. En el **acciones del sitio** menú, elija **configuración del sitio** para mostrar la página Configuración del sitio.  
  
10. En el **galerías** sección, elija el **columnas de sitio** vínculo.  
  
11. En la parte superior de la **Galería de columnas de sitio** página, elija la **crear** botón.  
  
12. En el **nombre de la columna** cuadro, escriba **columna prueba**, mantenga los demás valores predeterminados y, a continuación, elija la **Aceptar** botón.  
  
13. El **columna prueba** columna aparece debajo de las columnas personalizadas encabezada en la Galería de columnas de sitio.  
  
## <a name="exporting-the-sharepoint-site"></a>Exportar el sitio de SharePoint  
 A continuación, obtener un archivo de instalación (.wsp) de SharePoint que contiene los elementos de SharePoint y los elementos que se van a importar en el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint. Si no dispone de un archivo .wsp, debe crear uno desde un sitio de SharePoint existente. En este ejemplo, exportará el sitio de SharePoint de forma predeterminada en un archivo .wsp.  
  
> [!IMPORTANT]  
>  Si recibe un error en tiempo de ejecución lleva a cabo el procedimiento siguiente, tendrá que llevar a cabo el procedimiento en un sistema que tiene acceso al sitio de SharePoint.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>Para exportar un sitio de SharePoint existente  
  
1.  En el sitio de SharePoint, elija **configuración del sitio** en el **acciones del sitio** ficha para mostrar la página Configuración del sitio.  
  
2.  En el **acciones del sitio** sección de la página Configuración del sitio, elija la **Guardar sitio como plantilla** vínculo.  
  
3.  En el **nombre de archivo** cuadro, escriba **SitioEjemplo**y en el **nombre de la plantilla** cuadro, escriba **ejemplo sitio**.  
  
4.  En este ejemplo, deje el **incluir contenido** casilla de verificación.  
  
     Si activa esta casilla, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] guarda todas las listas y bibliotecas de documentos y su contenido, en el archivo .wsp. Aunque esto es útil en algunas circunstancias, no es necesario para este ejemplo.  
  
5.  Cuando la operación se completa correctamente, elija la **Galería de soluciones** vínculo para ver el archivo .wsp.  
  
     Para ver la página de la Galería de soluciones más adelante, abra el **acciones del sitio** menú, elija **configuración del sitio**, elija la **vaya a configuración del sitio de nivel superior** vincular en el  **Administración de la colección de sitios** sección y, a continuación, elija la **soluciones** vincular en el **galerías** sección.  
  
6.  En la Galería de soluciones, elija la **SitioEjemplo** vínculo.  
  
7.  En el **descarga de archivos** diálogo cuadro, elija la **guardar** botón para guardar el archivo en el sistema local, de forma predeterminada, en la carpeta de descargas.  
  
## <a name="importing-the-wsp-file"></a>Importar el archivo .wsp  
 Ahora que tiene un archivo .wsp que contiene un elemento que desea reutilizar (la columna de sitio personalizada columna prueba), importe el archivo .wsp para tener acceso a él.  
  
#### <a name="to-import-a-wsp-file"></a>Para importar un archivo .wsp  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menús, elija **archivo**, **New**, **proyecto** para mostrar la **nuevo proyecto** cuadro de diálogo. Si su IDE está configurado para usar la configuración de desarrollo de Visual Basic, en la barra de menús, elija **archivo**, **nuevo proyecto**.  
  
2.  Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija la **2010** nodo.  
  
3.  Elija la **Importar paquete de solución de SharePoint 2010** plantilla en el **plantillas** panel, deje el nombre del proyecto como WspImportProject1 y, a continuación, elija la **Aceptar** botón.  
  
     El **Asistente para personalización de SharePoint** aparece.  
  
4.  En el **especificar el nivel de sitio y la seguridad para la depuración** página, escriba la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el segundo subsitio de SharePoint que creó anteriormente. Agregará personalizado nuevo elemento, campo http://*nombre del sistema*/columntest2 a ese subsitio.  
  
5.  En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, deje la selección como **implementar como una solución en espacio aislado**.  
  
6.  En el **especifique el nuevo origen de proyecto** página, vaya a la ubicación en el sistema donde guardó el archivo .wsp previamente y, a continuación, elija la **siguiente** botón.  
  
    > [!NOTE]  
    >  Si elige la **finalizar** botón de esta página, todos los elementos disponibles en el archivo .wsp que se va a importar.  
  
7.  En el **seleccionar elementos para importar** cuadro, desactive todas las casillas de verificación en la lista, excepto para **columna prueba**y, a continuación, elija la **finalizar** botón.  
  
     Dado que la lista contiene muchos elementos, puede elegir las teclas Ctrl + una clave para elegir todos los elementos en la lista, presione la tecla barra espaciadora para borrar todas las casillas de verificación y, a continuación, active la casilla situada junto a la **columna prueba** elemento.  
  
     Una vez finalizada la operación de importación, un nuevo proyecto denominado **WspImportProject1** se crea que contiene una carpeta denominada **campos**. En esta carpeta es la columna de sitio personalizada **columna prueba** y su archivo de definición Elements.xml.  
  
## <a name="deploying-the-project"></a>Implementar el proyecto  
 Por último, implementar **WspImportProject1** en el segundo SharePoint subsitio que creó anteriormente para ver la columna de sitio personalizada.  
  
#### <a name="to-deploy-the-project"></a>Para implementar el proyecto  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], presione la tecla F5 para implementar y ejecutar el proyecto de importación wsp.  
  
2.  En el sitio de SharePoint, abra el **acciones del sitio** menú y, a continuación, elija **configuración del sitio** para mostrar la página Configuración del sitio.  
  
3.  En el **galerías** sección, elija el **columnas de sitio** vínculo.  
  
4.  Desplácese hacia abajo hasta la **columnas personalizadas** sección.  
  
     Observe que la columna de sitio personalizada que haya importado desde el primer sitio de SharePoint aparece en la lista.  
  
## <a name="see-also"></a>Vea también  
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  