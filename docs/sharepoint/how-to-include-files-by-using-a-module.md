---
title: 'Cómo: incluir archivos mediante un módulo | Microsoft Docs'
description: Sepa cómo incluir archivos mediante un módulo, que es un contenedor que permite implementar archivos como páginas maestras ASPX, archivos de texto o imágenes en SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 381cb529db3f4116a9c42041c26e0e1e242073df
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305411"
---
# <a name="how-to-include-files-by-using-a-module"></a>Cómo: para incluir archivos mediante un módulo
  Los *módulos* (que no se deben confundir con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] los módulos) son contenedores que permiten implementar archivos como páginas maestras aspx, archivos de texto o imágenes en SharePoint.

 Puede optar por implementar un archivo en una biblioteca de documentos o como un archivo normal (por ejemplo, default. aspx) fuera de una biblioteca de documentos. Para agregar un archivo a una biblioteca de documentos, especifique `Type="GhostableInLibrary"` como atributo en el elemento **File** . Esta configuración indica a SharePoint que cree un elemento de lista para ir al archivo cuando se agrega a la biblioteca. Para implementar un archivo fuera de una biblioteca de documentos, especifique `Type="Ghostable"` o simplemente omita el atributo **Type** .

## <a name="add-a-module-to-a-sharepoint-solution"></a>Agregar un módulo a una solución de SharePoint

#### <a name="to-add-a-module"></a>Para agregar un módulo

1. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , abra o cree un proyecto de SharePoint.

     Para obtener más información, vea [plantillas de proyecto y de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. En **Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

3. En la lista de plantillas de SharePoint, elija la plantilla de **módulo** y, a continuación, elija el botón **Agregar** .

     En este paso se crea un nodo en el proyecto denominado Module1.

4. En Module1, elimine el archivo de *Sample.txt* .

     Sample.txt se incluye en todos los módulos nuevos, por ejemplo, y no es necesario. (Tenga en cuenta que al eliminar el archivo también se quita la entrada del archivo de *Elements.xml* del módulo).

5. Si desea que los archivos se implementen en una estructura de carpetas determinada en SharePoint, cree esas carpetas en Module1 en eligiendo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] el nodo Module1 y, a continuación, en la barra de menús, elija **proyecto**, **nueva carpeta**.

6. Elija la carpeta en la que desea agregar el archivo y, a continuación, en la barra de menús, elija **proyecto**, **Agregar elemento existente**.

7. Elija uno o varios archivos que desee implementar en SharePoint y, a continuación, elija el botón **Agregar** .

     Cuando se agrega un archivo al proyecto, se agrega automáticamente una entrada al archivo Elements.xml del módulo. Cuando se implementa el proyecto, los archivos se copian en el servidor de SharePoint, en relación con el directorio raíz del proyecto, que se especifica mediante el atributo **URL** del elemento de **archivo** , como `Url="Module1/New Folder/SomeFile.doc` . Si desea cambiar la ubicación de implementación de un archivo, muévalo a otra carpeta de **Explorador de soluciones** o cambie la configuración de la **dirección URL** .

8. En el caso de los archivos que desee que aparezcan en una biblioteca de documentos, Anexe el `Type="GhostableInLibrary"` atributo a su entrada en *Elements.xml*. Por ejemplo,

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Implemente el proyecto.

     Los archivos se copian en las ubicaciones especificadas en SharePoint.

## <a name="see-also"></a>Consulte también
- [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
