---
title: "C&#243;mo: Importar un tema o p&#225;gina maestra"
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
  - "importar elementos [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, importar elementos"
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Importar un tema o p&#225;gina maestra
  Puede proporcionar a las páginas del sitio de SharePoint un aspecto coherente creando y páginas maestras y temas.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no proporciona plantillas para estos elementos, pero puede crearlos en SharePoint Designer y después importarlos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Para obtener más información, vea [Bloque de creación: Páginas e interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=182095) en el sitio Web de Microsoft.  
  
### Para importar un tema o una página maestra  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree o abra un proyecto de SharePoint.  
  
     Para obtener información sobre cómo crear un proyecto de SharePoint, vea [Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010**.  
  
4.  En la lista de plantillas de SharePoint, elija la plantilla de **Módulo** , y especifique un nombre para el módulo.  
  
     Un módulo contiene archivos \(por ejemplo, página maestra o archivos de tema\) para la implementación en una ubicación que especifique en SharePoint.  
  
5.  En el módulo, elimine el archivo predeterminado, que se denomina Sample.txt.  
  
6.  Elija el nodo módulo.  
  
7.  En la barra de menú, elija **Project**, **Agregar elemento existente**, y elija el archivo de página maestra o de tema.  
  
     Los archivos de página maestra tienen una extensión .master, y los archivos de tema tienen una extensión de .thmx.  
  
8.  Si ha agregado una página maestra, cambie su **Resolución de conflictos de implementación** a **Automático** en las propiedades del agente.  
  
    > [!NOTE]  
    >  Se pueden producir errores si el nombre de la página maestra es el mismo que el de una página maestra existente marcada como página maestra predeterminada o página maestra personalizada.  Para obtener información sobre cómo resolver este problema, vea [Tutorial: Importar una página maestra personalizada y una página de sitio con una imagen](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. En el módulo, abra Elements.xml.  
  
     Debe actualizar el archivo Elements.xml para que haga referencia a la página maestra o el tema que agregó.  
  
10. Para una página maestra, reemplace el marcado de módulo existente con el siguiente marcado.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Para un tema, reemplace el marcado de módulo existente con el siguiente marcado.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Asegúrese de reemplazar los valores de marcador de posición con los nombres reales del módulo y de la página maestra o el tema.  
  
     El atributo `Type="GhostableInLibrary"` indica que el elemento se ha agregado a la base de datos de contenido y el atributo `Url` del módulo especifica dónde se almacena el archivo en la base de datos de contenido de SharePoint.  
  
11. Para cambiar el ámbito de implementación de una página maestra, en **Explorador de soluciones**, abra el archivo de la característica Designer y, a continuación un nuevo ámbito de implementación de la lista de **Ámbito** .  
  
     Un valor de **web** significa que la página maestra sólo se aplica al sitio Web especificado actualmente en el proyecto.  Un valor de **sitio** significa que la página maestra se aplica a la colección de sitios actual, que incluye todos los subsitios y el sitio web raíz.  Los otros valores no se aplican.  
  
    > [!NOTE]  
    >  Dado que los temas solo se aplican en el nivel de colección de sitios, se recomienda no establecer el ámbito de un tema en un valor distinto de **sitio**.  Se pueden producir errores si se usa un tema en un subsitio.  
  
12. En la barra de menú, elija **Compilación**, **Implementar solución**.  
  
13. Para comprobar si los archivos se implementaron correctamente, abra el sitio de SharePoint, elegir el menú de **Acciones del sitio** , elegir el comando de **Configuración del sitio** , y a continuación elija el vínculo de **Páginas maestras** o vínculo de **temas;aspecto;apariencia** .  
  
     La lista de páginas maestras ni de temas aparece y contiene la página maestra o el tema importado.  
  
## Vea también  
 [Páginas maestras](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Crear páginas para SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Utilizar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  