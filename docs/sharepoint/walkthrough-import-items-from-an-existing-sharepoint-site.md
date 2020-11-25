---
title: 'Tutorial: importar elementos de un sitio de SharePoint existente | Microsoft Docs'
titleSuffix: ''
description: En este tutorial, importar elementos de un sitio de SharePoint existente en un proyecto de Visual Studio SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7eeff880538d98f997f48f82c49d01045e834031
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970138"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Tutorial: Importación de elementos desde un sitio de SharePoint existente
  En este tutorial se muestra cómo importar elementos de un sitio de SharePoint existente en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint.

 En este tutorial se muestran las siguientes tareas:

- Personalizar un sitio de SharePoint mediante la adición de una columna de sitio personalizada (también conocida como *campo*).

- Exportar un sitio de SharePoint a un archivo. wsp.

- Importar el archivo. wsp en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint mediante el proyecto de importación. wsp.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint.

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>Personalizar un sitio de SharePoint
 En este ejemplo, creará y personalizará un subsitio de SharePoint agregando una nueva columna de sitio a este y creando otro subsitio para usarlo más adelante. Posteriormente, exportará el primer subsitio a un archivo. wsp y, a continuación, importará la columna de sitio personalizado en el segundo subsitio mediante el proyecto de importación. wsp.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Para crear y personalizar un sitio de SharePoint

1. Abra un sitio de SharePoint mediante un explorador Web, como http://<em>nombre del sistema</em>/SitePages/Home.aspx.

2. Cree un subsitio fuera del sitio principal de SharePoint; para ello, abra el menú **acciones del sitio** y, a continuación, elija **nuevo sitio**.

3. En el cuadro de diálogo **crear** del sitio, elija el tipo de **sitio en blanco** .

4. En el cuadro **título** , escriba **prueba de columna de sitio 1**; en el cuadro **nombre de dirección URL** , escriba **columntest1**; Deje las demás opciones con sus valores predeterminados. y, a continuación, elija el botón **crear** .

5. Una vez creado el sitio, navegue en el explorador de nuevo al sitio principal, http://<em>nombre del sistema</em>/SitePages/Home.aspx.

6. De nuevo, cree un subsitio en blanco fuera del sitio principal de SharePoint; para ello, abra el menú **acciones del sitio** , elija **nuevo sitio** y, a continuación, elija el tipo de **sitio en blanco** .

7. En el cuadro **título** , escriba **site Column Test 2**; en el cuadro **nombre de dirección URL** , escriba **columntest2**; Deje las demás opciones con sus valores predeterminados. y, a continuación, elija el botón **crear** .

8. Vuelva al primer subsitio, http://<em>SystemName</em>/columntest1/default.aspx.

9. En el menú **acciones del sitio** , elija Configuración del **sitio** para mostrar la página Configuración del sitio.

10. En la sección **galerías** , elija el vínculo **columnas de sitio** .

11. En la parte superior de la página **Galería de columnas de sitio** , elija el botón **crear** .

12. En el cuadro **nombre de columna** , escriba columna de **prueba**, mantenga los demás valores predeterminados y elija el botón **Aceptar** .

13. La columna **columna de prueba** aparece en el encabezado columnas personalizadas de la galería de columnas de sitio.

## <a name="exporting-the-sharepoint-site"></a>Exportar el sitio de SharePoint
 A continuación, obtenga un archivo de instalación de SharePoint (. wsp) que contenga los elementos y elementos de SharePoint que desea importar en el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de SharePoint. Si aún no tiene un archivo. wsp, debe crear uno a partir de un sitio de SharePoint existente. En este ejemplo, exportará el sitio de SharePoint predeterminado a un archivo. wsp.

> [!IMPORTANT]
> Si recibe un error de tiempo de ejecución que realiza el procedimiento siguiente, tendrá que realizar el procedimiento en un sistema que tenga acceso al sitio de SharePoint.

### <a name="to-export-an-existing-sharepoint-site"></a>Para exportar un sitio de SharePoint existente

1. En el sitio de SharePoint, elija **configuración del sitio** en la pestaña acciones del **sitio** para mostrar la página Configuración del sitio.

2. En la sección **acciones del sitio** de la página Configuración del sitio, elija el vínculo **Guardar sitio como plantilla** .

3. En el **cuadro Nombre de archivo** , escriba **ExampleSite** y, en el cuadro Nombre de **plantilla** , escriba sitio de **ejemplo**.

4. En este ejemplo, deje desactivada la casilla **incluir contenido** .

     Si selecciona esta casilla, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] guarda todas las listas y bibliotecas de documentos, así como su contenido, en el archivo. wsp. Aunque esto es útil en algunas circunstancias, no es necesario para este ejemplo.

5. Cuando la operación se complete correctamente, elija el vínculo **Galería de soluciones** para ver el archivo. wsp.

     Para ver la página de la galería de soluciones más adelante, abra el menú **acciones del sitio** , elija **configuración del sitio**, elija el vínculo **ir al nivel superior configuración del sitio** en la sección Administración de la colección de **sitios** y, a continuación, elija el vínculo **soluciones** en la sección **galerías** .

6. En la galería de soluciones, elija el vínculo **ExampleSite** .

7. En el cuadro de diálogo **descarga de archivos** , elija el botón **Guardar** para guardar el archivo en el sistema local, de forma predeterminada, en la carpeta descargas.

## <a name="import-the-wsp-file"></a>Importar el archivo. wsp
 Ahora que tiene un archivo *. wsp* que contiene un elemento que desea volver a usar (la columna de prueba de columna de sitio personalizada), importe el archivo *. wsp* para tener acceso a él.

### <a name="to-import-a-wsp-file"></a>Para importar un archivo. wsp

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , en la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto** para mostrar el cuadro de diálogo **nuevo proyecto** . Si el IDE está establecido para usar la configuración de desarrollo de Visual Basic, en la barra de menús, elija **archivo**  >  **nuevo proyecto**.

2. Expanda el nodo **SharePoint** en **Visual C#** o **Visual Basic** y, a continuación, elija el nodo **2010** .

3. Elija la plantilla **importar paquete de solución de SharePoint 2010** en el panel **plantillas** , deje el nombre del proyecto como WspImportProject1 y, a continuación, elija el botón **Aceptar** .

    Aparece el **Asistente para la personalización de SharePoint** .

4. En la página **especifique el sitio y el nivel de seguridad de la depuración** , escriba [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el segundo subsitio de SharePoint que creó anteriormente. Agregará el nuevo elemento de campo personalizado, http://<em>nombre del sistema</em>/columntest2, a ese subsitio.

5. En la sección **¿cuál es el nivel de confianza de esta solución de SharePoint?** , deje la selección como **implementar como una solución en espacio aislado**.

6. En la página **especificar el origen del nuevo proyecto** , busque la ubicación en el sistema donde guardó el archivo *. wsp* previamente y, a continuación, elija el botón **siguiente** .

   > [!NOTE]
   > Si elige el botón **Finalizar** en esta página, se importarán todos los elementos disponibles en el archivo *. wsp* .

7. En el cuadro **seleccionar elementos para importar** , desactive todas las casillas de la lista excepto **columna de prueba** y, a continuación, elija el botón **Finalizar** .

    Dado que la lista contiene muchos elementos, puede elegir la tecla **Ctrl** + **a** teclas para elegir todos los elementos de la lista, elegir la tecla barra espaciadora para desactivar todas las casillas y, a continuación, activar solo la casilla situada junto al elemento de la **columna de prueba** .

    Una vez finalizada la operación de importación, se crea un nuevo proyecto denominado **WspImportProject1** que contiene una carpeta denominada **Fields**. En esta carpeta se encuentra la columna de **prueba** de columna de sitio personalizada y su archivo de definición *Elements.xml*.

## <a name="deploy-the-project"></a>Implementación del proyecto
 Por último, implemente **WspImportProject1** en el segundo subsitio de SharePoint que creó anteriormente para ver la columna de sitio personalizado.

### <a name="to-deploy-the-project"></a>Para implementar el proyecto

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , elija la tecla **F5** para implementar y ejecutar el proyecto de importación *. wsp* .

2. En el sitio de SharePoint, abra el menú **acciones del sitio** y, a continuación, elija **configuración** del sitio para mostrar la página Configuración del sitio.

3. En la sección **galerías** , elija el vínculo **columnas de sitio** .

4. Desplácese hacia abajo hasta la sección **columnas personalizadas** .

     Observe que en la lista aparece la columna de sitio personalizado que importó desde el primer sitio de SharePoint.

## <a name="see-also"></a>Vea también
- [Importación de elementos desde un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Creación de controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
