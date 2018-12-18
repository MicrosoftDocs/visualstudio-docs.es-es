---
title: 'Cómo: incluir archivos mediante un módulo | Microsoft Docs'
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
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c5152221e5e58504ba84e0ad0f31511b4d93aa0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119379"
---
# <a name="how-to-include-files-by-using-a-module"></a>Cómo: incluir archivos mediante un módulo
  *Módulos* (para que no se debe confundir con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos) son contenedores que permiten implementar imágenes, archivos de texto o archivos como páginas maestras de ASPX en SharePoint.  
  
 Puede elegir implementar un archivo en una biblioteca de documentos o como un archivo normal (por ejemplo, default.aspx) fuera de una biblioteca de documentos. Para agregar un archivo a una biblioteca de documentos, especifique `Type="GhostableInLibrary"` como un atributo en el **archivo** elemento. Esta opción indica que la creación de un elemento de lista que acompañe al archivo cuando se agrega a la biblioteca de SharePoint. Para implementar un archivo fuera de una biblioteca de documentos, especifique `Type="Ghostable"` o simplemente omita el **tipo** atributo.  
  
## <a name="add-a-module-to-a-sharepoint-solution"></a>Agregar un módulo a una solución de SharePoint  
  
#### <a name="to-add-a-module"></a>Para agregar un módulo  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra o cree un proyecto de SharePoint.  
  
     Para obtener más información, consulte [SharePoint plantillas de elemento de proyecto y](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto** > **Agregar nuevo elemento**.  
  
     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.  
  
3.  En la lista de plantillas de SharePoint, elija el **módulo** plantilla y, a continuación, elija el **agregar** botón.  
  
     Este paso crea un nodo en el proyecto denominado Module1.  
  
4.  En Module1, elimine el *Sample.txt* archivo.  
  
     Sample.txt se incluye en todos los módulos nuevos como ejemplo y no es necesaria. (Tenga en cuenta que al eliminar el archivo también quita su entrada del módulo *Elements.xml* archivo.)  
  
5.  Si desea que los archivos para implementar en una estructura de carpetas determinada en SharePoint, cree esas carpetas bajo Module1 en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] seleccionando el nodo Module1 y, a continuación, en la barra de menús, elija **proyecto**, **nuevo Carpeta**.  
  
6.  Elija la carpeta en la que desea agregar el archivo y, a continuación, en la barra de menús, elija **proyecto**, **Agregar elemento existente**.  
  
7.  Elija uno o varios archivos que desea implementar en SharePoint y, a continuación, elija el **agregar** botón.  
  
     Cuando se agrega un archivo al proyecto, se agrega automáticamente una entrada al archivo Elements.xml del módulo. Cuando se implementa el proyecto, los archivos se copian en el servidor de SharePoint, relativa al directorio raíz del proyecto, que se especifica mediante el **archivo** del elemento **Url** atributo, como `Url="Module1/New Folder/SomeFile.doc`. Si desea cambiar la ubicación de implementación de un archivo, ya sea moverlo a otra carpeta en **el Explorador de soluciones** o cambiar su **Url** configuración.  
  
8.  Para los archivos que desea que aparezca en una biblioteca de documentos, anexe el `Type="GhostableInLibrary"` a su entrada en el atributo *Elements.xml*. Por ejemplo,  
  
    ```xml  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Implemente el proyecto.  
  
     Copie los archivos en las ubicaciones especificadas en SharePoint.  
  
## <a name="see-also"></a>Vea también
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
