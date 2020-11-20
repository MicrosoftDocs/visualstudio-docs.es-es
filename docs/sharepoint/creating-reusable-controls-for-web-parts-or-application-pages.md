---
title: Creación de controles reutilizables para elementos web o páginas de aplicación | Microsoft Docs
titleSuffix: ''
description: Cree controles personalizados y reutilizables (controles de usuario) en Visual Studio que se pueden usar en las páginas de aplicación y los elementos web que se ejecutan en SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e9d2f3a99e3e43ebf40208bf8dfc01d5ac92dca
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850603"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Creación de controles reutilizables para elementos web o páginas de aplicación
  En Visual Studio, puede crear controles personalizados y reutilizables que se pueden usar en las páginas de aplicación y los elementos web que se ejecutan en SharePoint. Estos controles se denominan controles de usuario. Un control de usuario es un tipo de control compuesto que funciona de forma muy parecida a una página web de ASP.NET: puede agregar controles de servidor web y marcado existentes a un control de usuario, así como definir propiedades y métodos para el control. Después, puede insertarlos en páginas web de ASP.NET, donde actúan como una unidad.

## <a name="create-a-user-control"></a>Creación de un control de usuario
 Para crear un control de usuario, agregue un **Control de usuario** a un **proyecto vacío de SharePoint**. Para obtener más información, vea [Cómo: para crear un control de usuario para una página de aplicación o elemento web de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Al agregar un elemento **Control de usuario**, Visual Studio crea una carpeta en el proyecto y después le agrega varios archivos. En la tabla siguiente se describe cada archivo.

|Archivo|Descripción|
|----------|-----------------|
|Archivo de control de usuario|Define el control de usuario. Para diseñar el control de usuario, agregue controles y marcado a este archivo.|
|Archivo de código|Contiene código subyacente al control de usuario. Agregue código para controlar eventos en este archivo.|
|Archivo de código de diseñador|Contiene código generado por el diseñador y no se debe editar directamente.|

## <a name="design-the-user-control"></a>Diseño del control de usuario
 Diseñe el control de usuario mediante el diseñador Visual Web Developer de Visual Studio. Este diseñador aparece al abrir el archivo de control de usuario en el proyecto y elegir la pestaña **Diseño**.

## <a name="consume-the-user-control"></a>Consumo del control de usuario
 Los controles de usuario no aparecen en SharePoint hasta que los incluya en una página de aplicación o en un elemento web.

 Para incluir un control de usuario en una página de aplicación, abra la página web a la que quiera agregar el control de usuario de ASP.NET. Cambie a la vista Diseño, seleccione el archivo de control de usuario personalizado en el Explorador de soluciones y arrástrelo hasta la página. El control de usuario de ASP.NET se agrega a la página y el diseñador crea la directiva @ Register, que es necesaria para que la página reconozca el control de usuario. Ahora puede trabajar con las propiedades y los métodos públicos del control.

 Para incluir un control de usuario en un elemento web, agregue el control de usuario a la colección <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> de elementos web en el archivo de código del elemento web. En el ejemplo siguiente se agrega un control de usuario a la colección <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> de un elemento web.

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>Depuración de un control de usuario
 Para depurar un control de usuario, asegúrese de que esté incluido en una página de aplicación o en un elemento web del proyecto de SharePoint. Después, puede depurar el código en el control de usuario como haría con el de cualquier proyecto de Visual Studio.

 Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.

 En SharePoint, abra la página de la aplicación en la que se incluye el control de usuario. Si el control de usuario está incluido en un elemento web, agregue el elemento web a una página de elementos web en SharePoint.

 Para obtener más información sobre la depuración de proyectos de SharePoint, vea [Solución de problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: para crear un control de usuario para una página de aplicación o elemento web de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Se muestra cómo crear controles personalizados y reutilizables que se pueden usar en las páginas de aplicación y los elementos web que se ejecutan en SharePoint.|
