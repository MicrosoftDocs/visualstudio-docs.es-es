---
title: 'Tutorial: Importar elementos de un sitio de SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86256cdecd878c78c34d7128a05eb7b795067701
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909762"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Tutorial: Importar elementos de un sitio de SharePoint existente
  Este tutorial muestra cómo importar elementos de un sitio de SharePoint existente en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint.  
  
 En este tutorial se muestran las siguientes tareas:  
  
- Personalización de un sitio de SharePoint mediante la adición de una columna de sitio personalizada (también conocido como un *campo*.  
  
- Exportación de un sitio de SharePoint a un archivo WSP.  
  
- Importar el archivo .wsp en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint con el proyecto de importación de wsp.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.  
  
-   Visual Studio.  
  
## <a name="customize-a-sharepoint-site"></a>Personalizar un sitio de SharePoint
 En este ejemplo, creará y personalizar un subsitio de SharePoint agregando una nueva columna de sitio a él y creando otro subsitio para su uso posterior. Más adelante, exportará el primer subsitio a un archivo .wsp y, a continuación, importar la columna de sitio personalizado en el segundo subsitio usando el proyecto de importación de wsp.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Para crear y personalizar un sitio de SharePoint  
  
1. Abrir un sitio de SharePoint mediante un explorador Web, como http://<em>nombre del sistema</em>  /SitePages/Home.aspx.  
  
2. Crear un subsitio fuera del sitio principal de SharePoint abriendo la **acciones del sitio** menú y, a continuación, elija **nuevo sitio**.  
  
3. En la carpeta del sitio **crear** diálogo cuadro, elija el **sitio en blanco** tipo.  
  
4. En el **título** , escriba **prueba 1 de la columna de sitio**; en el **nombre URL** , escriba **columntest1**; deje los restantes valores en su valor predeterminado valores; y, a continuación, elija el **crear** botón.  
  
5. Una vez creado el sitio, navegue en el explorador al sitio principal, http://<em>nombre del sistema</em>  /SitePages/Home.aspx.  
  
6. De nuevo, crear un subsitio en blanco fuera del sitio principal de SharePoint abriendo la **acciones del sitio** menú, elegir **nuevo sitio**y, a continuación, elija el **sitio en blanco** tipo.  
  
7. En el **título** , escriba **prueba 2 de la columna de sitio**; en el **nombre URL** , escriba **columntest2**; deje los restantes valores en su valor predeterminado valores; y, a continuación, elija el **crear** botón.  
  
8. Vuelva a la primera subsitio, http://<em>SystemName</em>/columntest1/default.aspx.  
  
9. En el **acciones del sitio** menú, elija **configuración del sitio** para mostrar la página Configuración del sitio.  
  
10. En el **galerías** sección, elija el **columnas de sitio** vínculo.  
  
11. En la parte superior de la **Galería de columnas de sitio** página, elija el **crear** botón.  
  
12. En el **nombre de columna** , escriba **columna prueba**, mantenga los demás valores predeterminados y, a continuación, elija el **Aceptar** botón.  
  
13. El **columna prueba** columna aparece debajo de las columnas personalizadas encabezada en la Galería de la columna de sitio.  
  
## <a name="exporting-the-sharepoint-site"></a>Exportar el sitio de SharePoint
 A continuación, obtener un archivo de instalación (.wsp) de SharePoint que contiene los elementos de SharePoint y los elementos que desea importar a su [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint. Si no dispone de un archivo .wsp, debe crear uno desde un sitio de SharePoint existente. En este ejemplo, exportará el sitio de SharePoint de forma predeterminada en un archivo WSP.  
  
> [!IMPORTANT]  
>  Si recibe un error en tiempo de ejecución realizar el procedimiento siguiente, deberá llevar a cabo el procedimiento en un sistema que tiene acceso al sitio de SharePoint.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>Para exportar un sitio de SharePoint existente  
  
1.  En el sitio de SharePoint, elija **configuración del sitio** en el **acciones del sitio** ficha para mostrar la página Configuración del sitio.  
  
2.  En el **acciones del sitio** sección de la página Configuración del sitio, elija el **sitio Guardar como plantilla** vínculo.  
  
3.  En el **nombre de archivo** , escriba **SitioEjemplo**y en el **nombre de la plantilla** , escriba **el sitio de ejemplo**.  
  
4.  En este ejemplo, deje el **incluir contenido** casilla de verificación.  
  
     Si activa esta casilla, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] guarda todas las listas y bibliotecas de documentos y su contenido, en el archivo WSP. Aunque esto es útil en algunas circunstancias, no es necesario para este ejemplo.  
  
5.  Cuando la operación se completa correctamente, elija el **Galería de soluciones** vínculo para ver el archivo WSP.  
  
     Para ver la página de la Galería de soluciones más adelante, abra el **acciones del sitio** menú, elija **configuración del sitio**, elija el **vaya a la configuración del sitio de nivel superior** vincular en el  **Administración de la colección de sitios** sección y, a continuación, elija el **soluciones** vincular en el **galerías** sección.  
  
6.  En la Galería de soluciones, elija el **SitioEjemplo** vínculo.  
  
7.  En el **de descarga del archivo** diálogo cuadro, elija el **guardar** botón para guardar el archivo en el sistema local, de forma predeterminada, en la carpeta descargas.  
  
## <a name="import-the-wsp-file"></a>Importar el archivo .wsp
 Ahora que tiene un *.wsp* archivo que contiene un elemento que desea volver a usar (la columna de sitio personalizada columna prueba), importe el *.wsp* archivos para acceder a él.  
  
#### <a name="to-import-a-wsp-file"></a>Para importar un archivo .wsp  
  
1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menús, elija **archivo** > **New** > **proyecto** para mostrar el **nuevo proyecto**cuadro de diálogo. Si el IDE está establecido para usar la configuración de desarrollo de Visual Basic, en la barra de menús, elija **archivo** > **nuevo proyecto**.  
  
2. Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija el **2010** nodo.  
  
3. Elija la **Importar paquete de solución de SharePoint 2010** plantilla en el **plantillas** panel, deje el nombre del proyecto como WspImportProject1 y, a continuación, elija el **Aceptar** botón.  
  
    El **Asistente de personalización de SharePoint** aparece.  
  
4. En el **especificar el nivel de sitio y de seguridad para la depuración** , escriba la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el segundo subsitio de SharePoint que creó anteriormente. Se agregará personalizado nuevo campo de elemento, http://<em>nombre del sistema</em>/columntest2 a ese subsitio.  
  
5. En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, deje la selección como **implementar como solución en espacio aislado**.  
  
6. En el **especificar el origen del nuevo proyecto** página, vaya a la ubicación en el sistema donde guardó el *.wsp* anteriormente y, a continuación, seleccione el **siguiente** botón.  
  
   > [!NOTE]  
   >  Si elige la **finalizar** botón en esta página, todos los elementos disponibles en el *.wsp* se importará el archivo.  
  
7. En el **seleccionar elementos para importar** cuadro, borre todas las casillas de verificación en la lista excepto **columna prueba**y, a continuación, elija el **finalizar** botón.  
  
    Dado que la lista contiene muchos elementos, puede elegir el **Ctrl**+**A** claves para elegir todos los elementos en la lista, elija la tecla barra espaciadora para borrar todas las casillas de verificación y, a continuación, seleccione solo la comprobación cuadro situado junto a la **columna prueba** elemento.  
  
    Una vez finalizada la operación de importación, un nuevo proyecto denominado **WspImportProject1** creado que contiene una carpeta denominada **campos**. En esta carpeta es la columna de sitio personalizada **columna prueba** y su archivo de definición *Elements.xml*.  
  
## <a name="deploy-the-project"></a>Implementar el proyecto
 Por último, implemente **WspImportProject1** en el segundo SharePoint subsitio que creó anteriormente para ver la columna de sitio personalizada.  
  
#### <a name="to-deploy-the-project"></a>Para implementar el proyecto  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], elija el **F5** clave para implementar y ejecutar el *.wsp* Importar proyecto.  
  
2.  En el sitio de SharePoint, abra el **acciones del sitio** menú y, a continuación, elija **configuración del sitio** para mostrar la página Configuración del sitio.  
  
3.  En el **galerías** sección, elija el **columnas de sitio** vínculo.  
  
4.  Desplácese hacia abajo hasta la **columnas personalizadas** sección.  
  
     Tenga en cuenta que la columna de sitio personalizada que haya importado desde el primer sitio de SharePoint aparece en la lista.  
  
## <a name="see-also"></a>Vea también
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
