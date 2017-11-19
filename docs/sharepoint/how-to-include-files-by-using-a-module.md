---
title: "Cómo: incluir archivos mediante un módulo | Documentos de Microsoft"
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
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 848fc50b8886cc736c5a7a856beec238c084d879
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-include-files-by-using-a-module"></a>Cómo: Incluir archivos mediante un módulo
  *Módulos* (no se deben confundir con [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] módulos) son contenedores que permiten implementar los archivos, como páginas maestras ASPX, archivos de texto o imágenes en SharePoint.  
  
 Puede elegir implementar un archivo en una biblioteca de documentos o como un archivo normal (por ejemplo, default.aspx) fuera de una biblioteca de documentos. Para agregar un archivo a una biblioteca de documentos, especifique `Type="GhostableInLibrary"` como un atributo en el **archivo** elemento. Esta opción indica que crear un elemento de lista que acompañe al archivo cuando se agrega a la biblioteca de SharePoint. Para implementar un archivo fuera de una biblioteca de documentos, especifique `Type="Ghostable"` o simplemente omita el **tipo** atributo.  
  
## <a name="adding-a-module-to-a-sharepoint-solution"></a>Agregar un módulo a una solución de SharePoint  
  
#### <a name="to-add-a-module"></a>Para agregar un módulo  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra o cree un proyecto de SharePoint.  
  
     Para obtener más información, consulte [proyecto de SharePoint y plantillas de elementos de proyecto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  En **el Explorador de soluciones**, elija el nodo del proyecto y, a continuación, en la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.  
  
3.  En la lista de plantillas de SharePoint, elija el **módulo** plantilla y, a continuación, elija la **agregar** botón.  
  
     Este paso crea un nodo en el proyecto denominado Module1.  
  
4.  En Module1, elimine el archivo Sample.txt.  
  
     Sample.txt se incluye en todos los módulos nuevos como ejemplo y no es necesaria. (Tenga en cuenta que también elimina el archivo quita su entrada de archivo Elements.xml del módulo.)  
  
5.  Si desea que los archivos para implementar en una estructura de carpetas determinada en SharePoint, cree esas carpetas bajo Module1 en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] seleccionando el nodo Module1 y, a continuación, en la barra de menús, elija **proyecto**, **New Carpeta**.  
  
6.  Elija la carpeta en la que desea agregar el archivo y, a continuación, en la barra de menús, elija **proyecto**, **Agregar elemento existente**.  
  
7.  Elija uno o varios archivos que desea implementar en SharePoint y, a continuación, elija la **agregar** botón.  
  
     Cuando se agrega un archivo al proyecto, se agrega automáticamente una entrada al archivo Elements.xml del módulo. Cuando se implementa el proyecto, los archivos se copian al servidor de SharePoint, relativa al directorio de raíz del proyecto, que se especifica mediante la **archivo** del elemento **Url** atributo, como `Url="Module1/New Folder/SomeFile.doc`. Si desea cambiar la ubicación de implementación de un archivo, ya sea mover a otra carpeta en **el Explorador de soluciones** o cambiar su **Url** configuración.  
  
8.  Para los archivos que desea que aparezca en una biblioteca de documentos, anexe el `Type="GhostableInLibrary"` atribuir a su entrada en Elements.xml. Por ejemplo,  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Implemente el proyecto.  
  
     Copie los archivos en las ubicaciones especificadas en SharePoint.  
  
## <a name="see-also"></a>Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  