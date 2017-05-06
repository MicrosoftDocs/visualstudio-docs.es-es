---
title: "C&#243;mo: Incluir archivos mediante un m&#243;dulo"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "módulos [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, módulos"
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# C&#243;mo: Incluir archivos mediante un m&#243;dulo
  Los *módulos* \(no deben confundirse con los módulos de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) son contenedores que permiten implementar archivos, como páginas maestras ASPX, archivos de texto o imágenes, en SharePoint.  
  
 Puede implementar un archivo en una biblioteca de documentos o como un archivo normal \(por ejemplo, default.aspx\) fuera de una biblioteca de documentos.  Para agregar un archivo a una biblioteca de documentos, especifique `Type="GhostableInLibrary"` como atributo en el elemento **File**.  Este valor le indica a SharePoint que debe crear un elemento de lista que acompañe al archivo cuando este se agregue a la biblioteca.  Para implementar un archivo fuera de una biblioteca de documentos, especifique `Type="Ghostable"` o simplemente omita el atributo **Type**.  
  
## Agregar un módulo a una solución de SharePoint  
  
#### Para agregar un módulo  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra o cree un proyecto de SharePoint.  
  
     Para obtener más información, vea [Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  En **Explorador de soluciones**, elija el nodo de proyecto y, a continuación, en la barra de menús, elija **Project**, **Agregar nuevo elemento**.  
  
     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.  
  
3.  En la lista de plantillas de SharePoint, elija la plantilla de **Módulo** , y elija el botón de **Add** .  
  
     Este paso crea un nodo del proyecto denominado Module1.  
  
4.  Bajo Module1, elimine el archivo Sample.txt.  
  
     Sample.txt se ha incluido en todos los módulos nuevos como ejemplo y no es un archivo necesario. \(Observe que al eliminar el archivo, también se quita su entrada del archivo Elements.xml del módulo\).  
  
5.  Si desea que los archivos se implementen en una estructura de carpetas de SharePoint determinada, cree esas carpetas bajo Module1 en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eligiendo el nodo Module1 y, a continuación, en la barra de menús, eligiendo **Project**, **Nueva carpeta**.  
  
6.  Elija la carpeta donde desea agregar el archivo y, a continuación, en la barra de menú, elija **Project**, **Agregar elemento existente**.  
  
7.  Elija uno o más archivos que desee implementar en SharePoint, y elija el botón de **Add** .  
  
     Cuando agrega un archivo al proyecto, se agrega automáticamente una entrada para él en el archivo Elements.xml del módulo.  Cuando se implementa el proyecto, los archivos se copian en el servidor de SharePoint \(de acuerdo con el directorio raíz del proyecto\) especificado por el atributo **Url** del elemento **File**, como por ejemplo `Url="Module1/New Folder/SomeFile.doc`.  Si desea cambiar la ubicación de implementación de un archivo, muévalo a otra carpeta del **Explorador de soluciones** o cambie su valor **Url**.  
  
8.  En los archivos que desea que aparezcan en una biblioteca de documentos, anexe el atributo `Type="GhostableInLibrary"` a su entrada en Elements.xml.  Por ejemplo,  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Implemente el proyecto.  
  
     Los archivos se copian en las ubicaciones de SharePoint especificadas.  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  