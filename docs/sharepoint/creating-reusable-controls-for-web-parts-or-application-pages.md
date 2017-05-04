---
title: "Crear controles reutilizables para elementos web o p&#225;ginas de aplicaci&#243;n | Microsoft Docs"
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
  - "desarrollo de SharePoint en Visual Studio, controles de usuario"
  - "controles de usuario [desarrollo de SharePoint en Visual Studio], crear"
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Crear controles reutilizables para elementos web o p&#225;ginas de aplicaci&#243;n
  En Visual Studio, puede crear una personalizada, controles reutilizables que pueden usar las páginas de la aplicación y los elementos web que se ejecutan en SharePoint.  Estos controles se denominan controles de usuario.  Para obtener más información acerca de los controles de usuario, vea [ASP.NET User Controls](../Topic/ASP.NET%20User%20Controls.md).  
  
## Crear un control de usuario  
 Para crear un control de usuario, agregue un **Control de usuario** a un **Proyecto de SharePoint vacío**.  Para obtener más información, vea [Cómo: Crear un control de usuario para una página de aplicación o elemento web de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Al agregar un elemento **Control de usuario**, Visual Studio crea una carpeta en su proyecto y le agrega varios archivos.  En la tabla siguiente se describe cada archivo.  
  
|Archivo|Descripción|  
|-------------|-----------------|  
|Archivo control de usuario|Define el control de usuario.  Diseñe el control de usuario agregando controles y marcado a este archivo.|  
|Archivo de código|Contiene código subyacente del control de usuario.  Agregue código para controlar los eventos a este archivo.|  
|Archivo de código del diseñador|Contiene código generado por el diseñador y no debe modificarse.|  
  
## Diseñar el control de usuario  
 Diseñe el control de usuario utilizando el diseñador de Visual Web Developer en Visual Studio.  Este diseñador aparece al abrir el archivo de control de usuario en el proyecto y elija la ficha de **Diseñar** .  Para obtener más información sobre cómo usar este diseñador, vea [Mapa de contenido del entorno de desarrollo web de Visual Studio](http://msdn.microsoft.com/es-es/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
## Utilizar el control de usuario  
 Los controles de usuario no aparecen en SharePoint hasta que no se incluyen en una página de aplicación o en un elemento web.  
  
 Para incluir un control de usuario en una página de aplicación, agregue una directiva [@ Register](http://msdn.microsoft.com/es-es/66f34922-be41-4e36-9dc8-1774d85311d1) a la página de aplicación y, a continuación, declare el control de usuario dentro de uno o más marcadores de posición de contenido en la página.  Para obtener un ejemplo de cómo lograr esta tarea en una página web ASP.NET estándar, vea [How to: Include a User Control in an ASP.NET Web Page](../Topic/How%20to:%20Include%20a%20User%20Control%20in%20an%20ASP.NET%20Web%20Page.md).  
  
 Para incluir un control de usuario en un elemento web, agréguelo a la colección <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> del archivo de código del elemento web.  En el ejemplo siguiente se muestra cómo agregar el control de usuario a la colección <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> de un elemento web.  
  
 [!code-csharp[SP_VisualWebPart#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1.cs#5)]
 [!code-vb[SP_VisualWebPart#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1.vb#5)]  
  
## Depurar un control de usuario  
 Para depurar un control de usuario, asegúrese de que está incluido en una página de aplicación o elemento web en el proyecto SharePoint.  Puede depurar código en el control de usuario del mismo modo que depuraría código en un proyecto de Visual Studio.  
  
 Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.  
  
 En SharePoint, abra la página de aplicación que incluye el control de usuario.  Si el control de usuario está incluido en un elemento web, agregue el elemento web a un página de elementos web en SharePoint.  
  
 Para obtener más información sobre la depuración de proyectos de SharePoint, vea [Solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Cómo: Crear un control de usuario para una página de aplicación o elemento web de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Muestra cómo se crean controles personalizados y reutilizables que se pueden usar en las páginas de aplicación y los elementos web que se ejecutan en SharePoint.|  
|[Trabajar con Visual Web Developer](http://msdn.microsoft.com/es-es/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Describe cómo utilizar el diseñador que aparece al abrir una página web en el proyecto.|  
  
  