---
title: 'Cómo: importar una página maestra o un tema | Microsoft Docs'
description: Cree plantillas para páginas maestras y temas en SharePoint Designer y, a continuación, importe en Visual Studio para dar a las páginas del sitio de SharePoint una apariencia coherente.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 331ae3964de40e6590345aadae59776fe37f467a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913671"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Cómo importar un tema o página maestra
  Puede dar una apariencia coherente a las páginas del sitio de SharePoint creando y usando páginas maestras y temas. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no proporciona plantillas para estos elementos, pero puede crearlos en SharePoint Designer y, a continuación, importarlos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Para obtener más información, vea [bloque de creación: páginas e interfaz de usuario](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) en el sitio web de Microsoft.

### <a name="to-import-a-master-page-or-theme"></a>Para importar un tema o página maestra

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , cree o abra un proyecto de SharePoint.

     Para obtener información sobre cómo crear un proyecto de SharePoint, vea plantillas de proyecto [y de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

4. En la lista de plantillas de SharePoint, elija la plantilla de **módulo** y, a continuación, especifique un nombre para el módulo.

     Un módulo contiene archivos (por ejemplo, archivos de página maestra o de tema) para la implementación en una ubicación que se especifica en SharePoint.

5. En el módulo, elimine el archivo predeterminado, que se denomina *Sample.txt*.

6. Elija el nodo del módulo.

7. En la barra de menús, elija **proyecto**  >  **Agregar elemento existente** y, a continuación, elija el archivo de tema o la página maestra.

     Los archivos de la página maestra tienen la extensión. Master y los archivos de tema tienen la extensión. thmx.

8. Si agregó una página maestra, cambie la configuración de **resolución de conflictos de implementación** a **automático** en las propiedades del módulo.

    > [!NOTE]
    > Pueden producirse errores si el nombre de la página maestra es el mismo que el nombre de una página maestra existente marcada como página maestra predeterminada o como página maestra personalizada. Para obtener información sobre cómo resolver este problema, vea [Tutorial: importar una página maestra personalizada y una página de sitio con una imagen](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).

9. En el módulo, Abra *Elements.xml*.

     Debe actualizar el archivo de *Elements.xml* para hacer referencia a la página maestra o al tema que ha agregado.

10. En el caso de una página maestra, reemplace el marcado del módulo existente por el marcado siguiente.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     Para un tema, reemplace el marcado del módulo existente por el marcado siguiente.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     Asegúrese de reemplazar los valores de marcador de posición por los nombres reales del módulo y la página maestra o el tema.

     El atributo `Type="GhostableInLibrary"` indica que el elemento se agrega a la base de datos de contenido y el `Url` atributo del módulo especifica dónde almacenar el archivo en la base de datos de contenido de SharePoint.

11. Para cambiar el ámbito de implementación de una página maestra, en **Explorador de soluciones**, abra el archivo de características en el diseñador de características y, a continuación, elija un nuevo ámbito de implementación en la lista **ámbito** .

     Un valor de **Web** significa que la página maestra solo se aplica al sitio Web especificado actualmente en el proyecto. Un valor de **sitio** significa que la página maestra se aplica a la colección de sitios actual, que incluye todos los subsitios y el Web raíz. Los demás valores no se aplican.

    > [!NOTE]
    > Dado que los temas se aplican solo al nivel de colección de sitios, se recomienda no establecer el ámbito de un tema en ningún elemento que no sea el **sitio**. Se pueden producir errores si se usa un tema en un subsitio.

12. En la barra de menús, elija **compilar**  >  **implementar solución**.

13. Para comprobar si los archivos se han implementado correctamente, abra el sitio de SharePoint, elija el menú **acciones del sitio** , elija el comando **configuración del sitio** y, a continuación, elija el vínculo **páginas maestras** o el vínculo **temas** .

     La lista de páginas maestras o temas aparece y contiene la página maestra o el tema que ha importado.

## <a name="see-also"></a>Vea también
- [Páginas maestras](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Creación de páginas para SharePoint](../sharepoint/creating-pages-for-sharepoint.md)
- [Uso de módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md)
