---
title: Crear elementos Web para SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1efe8524521be590e920818f919a7a52d8fba7e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879139"
---
# <a name="create-web-parts-for-sharepoint"></a>Crear elementos web para SharePoint
  Usando elementos web, puede modificar el contenido, el aspecto y el comportamiento de las páginas de un sitio de SharePoint a través de un explorador. Los elementos web son controles de servidor que se ejecutan dentro de una página de elementos web: son los bloques de creación de las páginas que aparecen en un sitio de SharePoint. Consulte [bloques de creación: Elementos Web](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Puede crear y depurar elementos web en un sitio de SharePoint mediante el uso de plantillas de Visual Studio.  
  
## <a name="create-a-web-part-in-visual-studio"></a>Crear un elemento web en Visual Studio
 Crear un elemento web agregando un **elemento Web** a un proyecto de SharePoint. Puede usar un **elemento Web** elemento en una solución en espacio aislado o una solución de granja de servidores.  
  
 Si desea diseñar un elemento web visualmente mediante un diseñador, cree un **elemento Web Visual** proyecto o agregue **elemento Web Visual** a un proyecto de SharePoint. Puede usar un **elemento Web Visual** elemento en sólo una solución de granja de servidores.  
  
### <a name="web-part-item"></a>Elemento de elemento Web
 Un **elemento Web** proporciona archivos que pueden utilizar para diseñar un elemento web para un sitio de SharePoint. Cuando se agrega un **elemento Web** elemento, Visual Studio crea una carpeta en el proyecto y, a continuación, agrega varios archivos a la carpeta. En la tabla siguiente se describe cada archivo.  
  
|Archivo|Descripción|  
|----------|-----------------|  
|*Elements.Xml*|Contiene información que utiliza el archivo de definición de características en el proyecto para implementar el elemento web.|  
|Archivo .webpart|Proporciona información que SharePoint necesita para mostrar el elemento web en una galería de elementos web.|  
|Archivo de código|Contiene métodos que agregan controles al elemento web y generan el contenido personalizado dentro del elemento web.|  
  
 Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Elemento web Visual
 Un elemento web visual es un elemento web que se crea utilizando el diseñador de Visual Web Developer en Visual Studio. Un elemento web visual funciona igual que cualquier otro elemento web. Para agregar controles, como botones y cuadros de texto, a elemento web, agregue código a un archivo XML. Sin embargo, agregar controles a un elemento web visual arrastrando o copiando en el elemento web de Visual Studio **cuadro de herramientas**. El diseñador entonces genera el código necesario en el archivo XML. Vea [Cómo: Crear elemento web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>Controles de SharePoint
 Visual Studio proporciona algunos controles para crear páginas de SharePoint, como páginas de aplicación. Estos controles aparecen en la **cuadro de herramientas** en **controles de SharePoint**. La funcionalidad para estos controles se deriva de la [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) espacio de nombres que contiene los controles de servidor ASP.NET que se usan en las páginas de sitio y lista de SharePoint.  
  
|Nombre del control|Descripción|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Inserta un menú de ASP. Para obtener más información, consulte [información general del Control de menú](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Inserta un **vínculo** elemento en el *.aspx* página y se aplica una o varias hojas de estilos externas definidas por **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Inserta un control de fecha y hora en la *.aspx* página.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Inserta una validación de seguridad en el *.aspx* página|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Devuelve una propiedad de una lista especificada.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Devuelve una propiedad global del sitio web actual.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Inserta un vínculo a una fuente RSS en la *.aspx* página.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Proporciona propiedades y métodos para registrar recursos, como scripts, en una página para que se puedan solicitar cuando se representa la página.|  
|[Tema](http://go.microsoft.com/fwlink/?LinkId=235314)|Se aplica un tema a la *.aspx* página.|  
  
## <a name="debug-a-web-part"></a>Depurar un elemento web
 Puede depurar un proyecto de SharePoint que contiene un elemento web igual que otros proyectos de Visual Studio. Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.  
  
 Para iniciar la depuración del código, agregue el elemento web a una página de elementos web de SharePoint.  
  
 Para obtener más información sobre cómo se depuran proyectos de SharePoint, vea [soluciones de SharePoint de la solución de problemas de](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Limitaciones de los elementos web visuales
 A partir de Visual Studio, puede agregar elementos web visuales a las soluciones en espacio aislado de SharePoint y a las soluciones de granja. Sin embargo, los elementos web visuales tienen las siguientes limitaciones:  
  
- Elementos web visuales no admiten parámetros reemplazables. Para obtener más información, consulte [parámetros reemplazables](../sharepoint/replaceable-parameters.md).  
  
- Los controles de usuario o elementos web visuales no se pueden arrastrar y quitar, o copiar sobre elementos web visuales. Esta acción provocará un error de compilación.  
  
- Los elementos web visuales no admiten directamente tokens del servidor de SharePoint como $SPUrl. Para obtener más información, vea "Token restricciones en espacio aislado elementos Web visuales" en el tema [soluciones de SharePoint de la solución de problemas de](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
- De vez en cuando, en los elementos web visuales en una solución de espacio aislado aparece el error, "Se rechazó la solicitud de ejecución de código de espacio aislado porque el servicio host de código de espacio aislado estaba demasiado ocupado para atender la solicitud". Para obtener más información sobre este error, vea esta entrada en el [blog del equipo de SharePoint Developer](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
- La depuración de JavaScript de servidor no se admite en Visual Studio, pero se admite la depuración de JavaScript de cliente.  
  
   Aunque se puede agregar JavaScript alineado en un archivo de marcado de servidor, no se admite la depuración en los puntos de interrupción agregados al marcado. Para depurar JavaScript, haga referencia a un archivo externo de JavaScript en el archivo de marcado y después establezca puntos de interrupción en el archivo JavaScript.  
  
- La depuración de código [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] alineado debe realizarse en el archivo de código generado en lugar de en el archivo de marcado.  
  
- Los elementos visuales web no admiten el uso de la directiva `<@ Assembly Src=`.  
  
- Los controles web de SharePoint y algunos controles de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] no se admiten en el entorno de SharePoint en espacio aislado. Si los controles no compatibles se utilizan en un elemento web visual en una solución en espacio aislado, aparece el error "El tipo o nombre del espacio de nombres 'Theme' no existe en el espacio de nombres 'Microsoft.SharePoint.WebControls'".  
  
  Para obtener más información acerca de las soluciones en espacio aislado, consulte [diferencias entre el espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="create-older-style-sharepoint-based-web-parts"></a>Crear el estilo anterior de elementos web basados en SharePoint
 Puede usar las plantillas de Visual Studio para crear elementos web de [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] personalizados para SharePoint. Los elementos web de [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] se compilan sobre la infraestructura de los elementos web de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] y son el tipo recomendado para los nuevos proyectos.  
  
 En muy pocos casos podría tener que crear un elemento web utilizando el elemento web del estilo anterior de SharePoint. Puede utilizar Visual Studio para crear estos tipos de elementos web, pero Visual Studio no proporciona plantillas diseñadas específicamente para ayudarle a crearlos.  
  
 Para obtener más información acerca de si desea crear un estilo anterior elemento web basado en SharePoint, vea [infraestructura de elementos Web en Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Para obtener más información sobre cómo crear un elemento web utilizando el estilo anterior elemento web basado en SharePoint, vea [tutorial de creación de un elemento Web de SharePoint básica](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>Temas relacionados
  
|Título|Descripción|  
|-----------|-----------------|  
|[Cómo: Crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Muestra cómo se crean elementos web para las páginas de SharePoint.|  
|[Cómo: Crear un elemento web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Muestra cómo se crean elementos web de SharePoint utilizando una superficie de diseño visual.|  
|[Cómo: Crear un control de usuario para un elemento de página o web de la aplicación de SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Muestra cómo se crean controles personalizados y reutilizables que se pueden usar en las páginas de aplicación y los elementos web que se ejecutan en SharePoint.|  
|[Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Describe cómo diseñar un elemento web para SharePoint.|  
|[Tutorial: Crear un elemento web para SharePoint utilizando un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Describe cómo se diseña un elemento web de SharePoint arrastrando controles a una superficie de diseño visual.|  
|[Tutorial: Crear elemento web de Silverlight que muestre OData para SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Describe cómo diseñar un elemento web para SharePoint que hospeda una aplicación de Silverlight y muestra datos de listas de SharePoint.|  
