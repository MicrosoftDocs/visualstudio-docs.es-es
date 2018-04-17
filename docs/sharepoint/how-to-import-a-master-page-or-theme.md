---
title: 'Cómo: importar un tema o página maestra | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: e60977a44593953b4858ea0262befc61c3189cec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-import-a-master-page-or-theme"></a>Cómo: Importar un tema o página maestra
  Puede dar páginas en el sitio de SharePoint una apariencia coherente mediante la creación y uso de temas y las páginas maestras. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no proporciona plantillas para estos elementos, pero puede crearlas en SharePoint Designer y, a continuación, importarlas en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulte [bloques de creación: interfaz de usuario y páginas](http://go.microsoft.com/fwlink/?LinkID=182095) en el sitio Web de Microsoft.  
  
### <a name="to-import-a-master-page-or-theme"></a>Para importar un tema o página maestra  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree o abra un proyecto de SharePoint.  
  
     Para obtener información sobre cómo crear un proyecto de SharePoint, vea [proyecto de SharePoint y plantillas de elementos de proyecto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
4.  En la lista de plantillas de SharePoint, elija el **módulo** plantilla y, a continuación, especifique un nombre para el módulo.  
  
     Un módulo contiene archivos (por ejemplo, página maestra o archivos de tema) para su implementación en una ubicación que especifique en SharePoint.  
  
5.  En el módulo, elimine el archivo de forma predeterminada, que es el nombre Sample.txt.  
  
6.  Elija el nodo de módulo.  
  
7.  En la barra de menús, elija **proyecto**, **Agregar elemento existente**y, a continuación, elija el archivo de tema o página maestra.  
  
     Archivos de página maestra tienen la extensión. master, y archivos de tema tienen una extensión .thmx.  
  
8.  Si ha agregado una página maestra, cambiar su **Deployment Conflict Resolution** si se establece en **automática** en las propiedades del módulo.  
  
    > [!NOTE]  
    >  Pueden producirse errores si el nombre de la página maestra es el mismo que el nombre de una página maestra existente que está marcado como página maestra predeterminada o página maestra personalizada. Para obtener información sobre cómo resolver este problema, consulte [Tutorial: importar una página maestra de personalizado y página del sitio con una imagen](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. En el módulo, abra Elements.xml.  
  
     Debe actualizar el archivo Elements.xml para hacer referencia a la página maestra o un tema que agregó.  
  
10. Para una página maestra, reemplace el marcado existente del módulo con el siguiente marcado.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Para un tema, reemplace el marcado existente del módulo con el marcado siguiente.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     No olvide reemplazar los valores de marcador de posición con los nombres reales de módulo y el tema o página maestra.  
  
     El atributo `Type="GhostableInLibrary"` indica que el elemento se agrega a la base de datos de contenido y el `Url` atributo del módulo especifica dónde desea almacenar el archivo en la base de datos de contenido de SharePoint.  
  
11. Para cambiar el ámbito de la implementación de una página maestra, en **el Explorador de soluciones**, abra el archivo de la característica en el Diseñador de características y, a continuación, elija un nuevo ámbito de implementación de la **ámbito** lista.  
  
     Un valor de **Web** significa que la página maestra se aplica solo al sitio Web que se especifica actualmente en el proyecto. Un valor de **sitio** significa que la página maestra se aplica a la colección de sitios actual, que incluye todos los subsitios y el sitio web raíz. No se aplican los demás valores.  
  
    > [!NOTE]  
    >  Dado que los temas se aplican sólo en el nivel de colección de sitios, se recomienda no establecer el ámbito de un tema en ningún otro valor distinto de **sitio**. Pueden producirse errores si se usa un tema en un sitio secundario.  
  
12. En la barra de menús, elija **generar**, **implementar solución**.  
  
13. Para comprobar si los archivos se implementaron correctamente, abra el sitio de SharePoint, elija el **acciones del sitio** menú, elija la **configuración del sitio** comando y, a continuación, elija la **páginas maestras**  vínculo o **temas** vínculo.  
  
     La lista de páginas maestras o temas aparece y contiene la página maestra o el tema que ha importado.  
  
## <a name="see-also"></a>Vea también  
 [Páginas maestras](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Crear páginas para SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Usar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  