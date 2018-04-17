---
title: Crear controles reutilizables para elementos Web o páginas de aplicación | Documentos de Microsoft
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
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e76a13174a9ac980644f8f9116c6518fc853028c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="creating-reusable-controls-for-web-parts-or-application-pages"></a>Crear controles reutilizables para elementos web o páginas de aplicación
  En Visual Studio, puede crear controles personalizados y reutilizables que pueden utilizarse en las páginas de aplicación y los elementos Web que se ejecutan en SharePoint. Estos controles se denominan controles de usuario. Un control de usuario es un tipo de control compuesto que funciona como una página Web ASP.NET, puede agregar controles de servidor Web existentes y el marcado para un control de usuario y definir propiedades y métodos para el control. A continuación, puede incrustarlos en páginas Web ASP.NET, que actúan como una unidad.  
  
## <a name="creating-a-user-control"></a>Crear un Control de usuario  
 Para crear un control de usuario, agregue un **Control de usuario** a una **proyecto vacío de SharePoint**. Para obtener más información, consulte [Cómo: crear un Control de usuario para un elemento Web o página de aplicación de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Cuando se agrega un **Control de usuario** elemento, crea una carpeta en el proyecto de Visual Studio y, a continuación, agrega varios archivos a la carpeta. En la tabla siguiente se describe cada archivo.  
  
|Archivo|Descripción|  
|----------|-----------------|  
|Archivo de control de usuario|Define el control de usuario. Diseñar el control de usuario agregando controles y marcado en este archivo.|  
|Archivo de código|Contiene código subyacente del control de usuario. Agregue código para controlar eventos en este archivo.|  
|Archivo de código del diseñador|Contiene código generado por el diseñador y no debe editarse directamente.|  
  
## <a name="designing-the-user-control"></a>Diseñar el Control de usuario  
 Diseñar el control de usuario mediante el Diseñador de Visual Web Developer en Visual Studio. Este diseñador aparece cuando se abra el archivo de control de usuario en el proyecto y elija la **diseño** ficha.  

## <a name="consuming-the-user-control"></a>Consumir el Control de usuario  
 Controles de usuario no aparecen en SharePoint hasta que se incluyan en una página de aplicación o un elemento Web.  
  
 Para incluir un control de usuario en una página de aplicación, abra la página Web a la que desea agregar el control de usuario ASP.NET. Cambie a la vista de diseño, a continuación, seleccione el archivo de control de usuario personalizado en el Explorador de soluciones y arrástrelo hasta la página. El control de usuario ASP.NET se agrega a la página y el diseñador crea la directiva @ Register, que es necesaria para la página para que reconozca el control de usuario. Ahora puede trabajar con los métodos y propiedades públicos del control.  
  
 Para incluir un control de usuario en un elemento Web, agregue el control de usuario para el elemento Web <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> colección en el archivo de código del elemento Web. En el ejemplo siguiente se agrega un control de usuario para el <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> colección de un elemento Web.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debugging-a-user-control"></a>Depurar un Control de usuario  
 Para depurar un control de usuario, asegúrese de que el control de usuario se incluye en una página de aplicación o un elemento Web en un proyecto de SharePoint. A continuación, puede depurar código en el control de usuario tal y como se haría código en cualquier proyecto de Visual Studio.  
  
 Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.  
  
 En SharePoint, abra la página de aplicación que incluye el control de usuario. Si el control de usuario se incluye en un elemento Web, agregue el elemento Web a una página de elemento Web de SharePoint.  
  
 Para obtener más información sobre la depuración de proyectos de SharePoint, vea [solución de problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Cómo: Crear un control de usuario para una página de aplicación o elemento web de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Muestra cómo crear controles personalizados y reutilizables que pueden utilizarse en las páginas de aplicación y los elementos Web que se ejecutan en SharePoint.|  
  
  