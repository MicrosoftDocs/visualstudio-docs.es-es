---
title: Creación de elementos web para SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3825ef7d2c1c90f63a90f5028063c74332543841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015047"
---
# <a name="create-web-parts-for-sharepoint"></a>Creación de elementos web para SharePoint
  Usando elementos web, puede modificar el contenido, el aspecto y el comportamiento de las páginas de un sitio de SharePoint a través de un explorador. Los elementos web son controles de servidor que se ejecutan dentro de una página de elementos web: son los bloques de creación de las páginas que aparecen en un sitio de SharePoint. Vea [Bloque de creación: elementos web](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Puede crear y depurar elementos web en un sitio de SharePoint mediante el uso de plantillas de Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Creación de un elemento web en Visual Studio
 Cree un elemento web mediante la adición de un elemento **Elemento web** a un proyecto de SharePoint. Puede usar un elemento **Elemento web** en una solución de espacio aislado o de granja de servidores.

 Si quiere diseñar un elemento web mediante un diseñador, cree un proyecto **Elemento web visual**, o bien agregue el elemento **Elemento web visual** a un proyecto de SharePoint. Solo puede usar un elemento **Elemento web visual** en una solución de granja de servidores.

### <a name="web-part-item"></a>Elemento de elemento web
 Un **Elemento web** proporciona archivos que puede usar para diseñar un elemento web para un sitio de SharePoint. Al agregar un elemento **Elemento web**, Visual Studio crea una carpeta en el proyecto y después le agrega varios archivos. En la tabla siguiente se describe cada archivo.

|Archivo|Descripción|
|----------|-----------------|
|*Elements.xml*|Contiene información que utiliza el archivo de definición de características en el proyecto para implementar el elemento web.|
|Archivo .webpart|Proporciona información que SharePoint necesita para mostrar el elemento web en una galería de elementos web.|
|Archivo de código|Contiene métodos que agregan controles al elemento web y generan el contenido personalizado dentro del elemento web.|

 Para obtener más información, vea [Cómo: para crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Elemento Elemento web visual
 Un elemento web visual es un elemento web que se crea utilizando el diseñador de Visual Web Developer en Visual Studio. Un elemento web visual funciona igual que cualquier otro elemento web. Para agregar controles, como botones y cuadros de texto, a elemento web, agregue código a un archivo XML. Pero para agregar controles a un elemento web visual debe arrastrarlos o copiarlos en el elemento web desde el **Cuadro de herramientas** de Visual Studio. El diseñador entonces genera el código necesario en el archivo XML. Vea [Cómo: para crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>Controles de SharePoint
 Visual Studio proporciona algunos controles para crear páginas de SharePoint, como páginas de aplicación. Estos controles aparecen en el **Cuadro de herramientas** en **Controles de SharePoint**. La funcionalidad para estos controles se deriva del espacio de nombres [Microsoft.SharePoint.WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)), que contiene controles de servidor ASP.NET que se usan en páginas de sitios y listas de SharePoint.

|Nombre del control|Descripción|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Inserta un menú de ASP. Para obtener más información, vea [Información general sobre el control Menú](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|Inserta un elemento **LINK** en la página *.aspx* y aplica una o varias hojas de estilos externas definidas por **CssRegistration**.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|Inserta un control DateTime en la página *.aspx*.|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|Inserta una validación de seguridad en la página *.aspx*.|
|[ListProperty](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Devuelve una propiedad de una lista especificada.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Devuelve una propiedad global del sitio web actual.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|Inserta un vínculo a una fuente RSS en la página *.aspx*.|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Proporciona propiedades y métodos para registrar recursos, como scripts, en una página para que se puedan solicitar cuando se representa la página.|
|[Tema](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|Aplica un tema a la página *.aspx*.|

## <a name="debug-a-web-part"></a>Depuración de un elemento web
 Puede depurar un proyecto de SharePoint que contiene un elemento web igual que otros proyectos de Visual Studio. Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.

 Para iniciar la depuración del código, agregue el elemento web a una página de elementos web de SharePoint.

 Para obtener más información sobre cómo depurar proyectos de SharePoint, vea [Solución de problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Limitaciones de los elementos web visuales
 A partir de Visual Studio, puede agregar elementos web visuales a las soluciones en espacio aislado de SharePoint y a las soluciones de granja. Sin embargo, los elementos web visuales tienen las siguientes limitaciones:

- Los elementos web visuales no admiten parámetros reemplazables. Para obtener más información, vea [Parámetros reemplazables](../sharepoint/replaceable-parameters.md).

- Los controles de usuario o elementos web visuales no se pueden arrastrar y quitar, o copiar sobre elementos web visuales. Esta acción provocará un error de compilación.

- Los elementos web visuales no admiten directamente tokens del servidor de SharePoint como $SPUrl. Para obtener más información, vea "Restricciones de token en elementos web visuales en espacio aislado" en el tema [Solución de problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

- De vez en cuando, en los elementos web visuales en una solución de espacio aislado aparece el error, "Se rechazó la solicitud de ejecución de código de espacio aislado porque el servicio host de código de espacio aislado estaba demasiado ocupado para atender la solicitud". Para obtener más información sobre este error, vea esta entrada en el [blog del equipo de desarrolladores de SharePoint](https://blogs.msdn.microsoft.com/sharepointdev/2011/02/08/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham/#10149157).

- La depuración de JavaScript de servidor no se admite en Visual Studio, pero se admite la depuración de JavaScript de cliente.

   Aunque se puede agregar JavaScript alineado en un archivo de marcado de servidor, no se admite la depuración en los puntos de interrupción agregados al marcado. Para depurar JavaScript, haga referencia a un archivo externo de JavaScript en el archivo de marcado y después establezca puntos de interrupción en el archivo JavaScript.

- La depuración de código [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] alineado debe realizarse en el archivo de código generado en lugar de en el archivo de marcado.

- Los elementos visuales web no admiten el uso de la directiva `<@ Assembly Src=`.

- Los controles web de SharePoint y algunos controles de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] no se admiten en el entorno de SharePoint en espacio aislado. Si los controles no compatibles se utilizan en un elemento web visual en una solución en espacio aislado, aparece el error "El tipo o nombre del espacio de nombres 'Theme' no existe en el espacio de nombres 'Microsoft.SharePoint.WebControls'".

  Para obtener más información sobre las soluciones en espacio, vea [Diferencias entre soluciones en espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Creación de elementos web basados en el estilo anterior de SharePoint
 Puede usar las plantillas de Visual Studio para crear elementos web de [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] personalizados para SharePoint. Los elementos web de [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] se compilan sobre la infraestructura de los elementos web de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] y son el tipo recomendado para los nuevos proyectos.

 En muy pocos casos podría tener que crear un elemento web utilizando el elemento web del estilo anterior de SharePoint. Puede utilizar Visual Studio para crear estos tipos de elementos web, pero Visual Studio no proporciona plantillas diseñadas específicamente para ayudarle a crearlos.

 Para obtener más información sobre cuándo le interesará crear un elemento web basado en un estilo anterior de SharePoint, vea [Infraestructura de elementos web en Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Para obtener más información sobre cómo crear un elemento web mediante el elemento web basado en el estilo anterior de SharePoint, vea [Tutorial para crear un elemento web básico de SharePoint](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: para crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Muestra cómo se crean elementos web para las páginas de SharePoint.|
|[Cómo: para crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Muestra cómo se crean elementos web de SharePoint utilizando una superficie de diseño visual.|
|[Cómo: para crear un control de usuario para una página de aplicación o elemento web de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Muestra cómo se crean controles personalizados y reutilizables que se pueden usar en las páginas de aplicación y los elementos web que se ejecutan en SharePoint.|
|[Tutorial: Creación de un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Describe cómo diseñar un elemento web para SharePoint.|
|[Tutorial: Creación de un elemento web para SharePoint mediante un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Describe cómo se diseña un elemento web de SharePoint arrastrando controles a una superficie de diseño visual.|
|[Tutorial: Creación de un elemento web de Silverlight que muestre OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Describe cómo diseñar un elemento web para SharePoint que hospeda una aplicación de Silverlight y muestra datos de listas de SharePoint.|
