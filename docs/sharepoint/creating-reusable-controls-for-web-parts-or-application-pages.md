---
title: Crear controles reutilizables para elementos web o páginas de aplicación | Microsoft Docs
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
ms.openlocfilehash: b174e1e16802838f19cec6dce727ea3199df730f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015142"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Crear controles reutilizables para elementos Web o páginas de aplicación
  En Visual Studio, puede crear controles personalizados y reutilizables que pueden usar las páginas de aplicación y elementos web que se ejecutan en SharePoint. Estos controles se denominan controles de usuario. Un control de usuario es un tipo de control compuesto que funciona de forma muy parecida a una página Web ASP.NET: puede Agregar controles de servidor Web y marcado existentes a un control de usuario, así como definir propiedades y métodos para el control. Después, puede insertarlos en páginas web de ASP.NET, donde actúan como una unidad.

## <a name="create-a-user-control"></a>Crear un control de usuario
 Para crear un control de usuario, agregue un **control de usuario** a un proyecto de **SharePoint vacío**. Para obtener más información, vea [Cómo: crear un control de usuario para una página de aplicación de SharePoint o un elemento Web](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Al agregar un elemento de **control de usuario** , Visual Studio crea una carpeta en el proyecto y, a continuación, agrega varios archivos a la carpeta. En la tabla siguiente se describe cada archivo.

|Archivo|Descripción|
|----------|-----------------|
|Archivo de control de usuario|Define el control de usuario. Diseñe el control de usuario agregando controles y marcado a este archivo.|
|Archivo de código|Contiene código subyacente al control de usuario. Agregue código para controlar los eventos de este archivo.|
|Archivo de código del diseñador|Contiene código generado por el diseñador y no debe editarse directamente.|

## <a name="design-the-user-control"></a>Diseñar el control de usuario
 Diseñe el control de usuario mediante el diseñador de Visual Web Developer en Visual Studio. Este diseñador aparece al abrir el archivo de control de usuario en el proyecto y elegir la pestaña **diseño** .

## <a name="consume-the-user-control"></a>Usar el control de usuario
 Los controles de usuario no aparecen en SharePoint hasta que los incluya en una página de aplicación o en un elemento Web.

 Para incluir un control de usuario en una página de aplicación, abra la página web a la que desea agregar el control de usuario ASP.NET. Cambie a Vista de diseño, seleccione el archivo de control de usuario personalizado en Explorador de soluciones y arrástrelo hasta la página. El control de usuario ASP.NET se agrega a la página y el diseñador crea la directiva @ Register, que es necesaria para que la página reconozca el control de usuario. Ahora puede trabajar con las propiedades y los métodos públicos del control.

 Para incluir un control de usuario en un elemento Web, agregue el control de usuario a la <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> colección de elementos Web en el archivo de código del elemento Web. En el ejemplo siguiente se agrega un control de usuario a la <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> colección de un elemento Web.

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>Depurar un control de usuario
 Para depurar un control de usuario, asegúrese de que el control de usuario está incluido en una página de aplicación o en un elemento Web del proyecto de SharePoint. Después, puede depurar el código en el control de usuario del mismo modo que depuraría el código en cualquier proyecto de Visual Studio.

 Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.

 En SharePoint, abra la página de la aplicación que incluye el control de usuario. Si el control de usuario está incluido en un elemento Web, agregue el elemento Web a una página de elementos Web en SharePoint.

 Para obtener más información sobre la depuración de proyectos de SharePoint, vea [solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: crear un control de usuario para una página de aplicación o elemento Web de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Muestra cómo crear controles personalizados y reutilizables que pueden usar las páginas de aplicación y elementos web que se ejecutan en SharePoint.|
