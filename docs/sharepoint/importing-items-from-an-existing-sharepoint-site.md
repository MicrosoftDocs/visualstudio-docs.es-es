---
title: Importar elementos de un sitio de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7435d6c7ad210554031994f4a366812f9799ffb2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832113"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Importar elementos de un sitio de SharePoint existente
  La plantilla de proyecto Importar paquete de solución de SharePoint permite reutilizar elementos, como tipos de contenido y campos de sitios de SharePoint existentes en una nueva [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solución de SharePoint. Aunque puede ejecutar la mayoría de las soluciones importadas sin modificaciones, hay algunas restricciones y aspectos a tener en cuenta, sobre todo si se modifican los elementos después de importarlos.  
  
> [!NOTE]  
>  Para importar flujos de trabajo reutilizables, use la plantilla de proyecto Importar flujo de trabajo reutilizable. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Pautas para importar flujos de trabajo reutilizables](../sharepoint/guidelines-for-importing-reusable-workflows.md).  
  
## <a name="supported-sharepoint-solutions"></a>Soluciones de SharePoint compatibles
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] es totalmente compatible con la importación de soluciones creadas en [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] y [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] no admite la importación de soluciones creadas en las siguientes aplicaciones:  
  
- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]  
  
- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]  
  
- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]  
  
- Microsoft SharePoint Designer 2007  
  
- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]  
  
  Aunque puede importar soluciones creadas por estas aplicaciones a menudo correctamente, esa funcionalidad no está probada y no es compatible.  
  
## <a name="item-import-restrictions"></a>Restricciones de importación de elemento
 Aunque la mayoría de los elementos de SharePoint se puede importar a partir de una máquina *.wsp* archivo, los elementos siguientes no se admiten y pueden requerir modificaciones para que funcionen correctamente:  
  
- Entidades BDC  
  
- Elementos de asociación de flujo de trabajo de código  
  
- Flujos de trabajo de código  
  
- Elementos web visuales (.ascx)  
  
- Servicios Web (*.asmx*)  
  
- Enlaces de tipo de contenido  
  
- Receptores de eventos  
  
- Definiciones de lista (plantillas)  
  
- Definiciones de sitio  
  
  Cuando se exporta una solución de [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] o [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], estos elementos se excluyen automáticamente de la *.wsp* archivo. Sin embargo, otros *.wsp* los archivos generados desde herramientas no compatibles pueden contener estos elementos. (Consulte "Soluciones de SharePoint compatibles" anteriormente en este tema).  
  
## <a name="what-happens-when-you-import-a-solution"></a>¿Qué ocurre al importar una solución
 Al importar una solución con la plantilla Importar paquete de solución de SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia todo el contenido de la *.wsp* archivos e intenta reconciliar y retener tantas asociaciones y referencias entre importado los elementos y sus archivos como sea posible.  
  
 Todos los elementos importados se copian en carpetas correspondientes en el **Explorador de soluciones**. Por ejemplo, los tipos de contenido aparecen en la carpeta **Tipos de contenido** y las instancias de la lista aparecen bajo **Lista de instancias**. Los archivos asociados a un elemento importado también se copian en la carpeta del elemento. Por ejemplo, una instancia de lista importada incluye sus módulos, formularios y páginas ASPX.  
  
### <a name="dependent-items"></a>Elementos dependientes
 Si selecciona un elemento en el Asistente para importar paquete de solución de SharePoint, pero no sus elementos dependientes, un cuadro de mensaje le informará de que los elementos dependientes también se deben activar antes de importar.  
  
### <a name="what-are-features"></a>¿Cuáles son las características?
 Los usuarios de SharePoint Designer pueden ver que archivos inusuales, denominados *características*, aparecen en las soluciones importadas en el **Explorador de soluciones.** Aunque las características existían en la solución de SharePoint Designer, estaban ocultas de la vista. Las características están ahora visibles en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Las características son contenedores de elementos de SharePoint. Cada característica mantiene una referencia a cada elemento, como tipos de contenido y las definiciones de lista que contiene. Al importar la solución, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] configura las características de todos los elementos importados e intenta mantener las relaciones característica-elemento de los archivos. Los archivos cuyas referencias no se podrían resolver se colocan en la carpeta **Otros archivos importados** .  
  
 Para obtener más información acerca de las características, consulte [soluciones de desarrollo de SharePoint](../sharepoint/developing-sharepoint-solutions.md) y [trabajar con características](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
### <a name="handle-special-cases"></a>Tratar los casos especiales
 En algunos casos, Visual Studio no puede reconciliar un elemento con sus archivos dependientes. Cualquier archivo que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no pudo resolver aparecen en la carpeta **Otros archivos importados**. Además, sus propiedades **DeploymentType** están establecidas en **NoDeployment** para que no se implementen con la solución.  
  
 Por ejemplo, si importa la definición de lista ExpenseForms, aparecerá una definición de lista con ese nombre en el **definiciones de la lista** carpeta **el Explorador de soluciones** junto con su  *Elements.XML* y *Schema.xml* archivos. Sin embargo, sus formularios ASPX y HTML asociados pueden colocarse en una carpeta llamada **ExpenseForms** en la carpeta **Otros archivos importados** . Para completar la importación, mueva estos archivos en la definición de lista ExpenseForms en el **Explorador de soluciones** y cambie la propiedad **DeploymentType** de cada archivo de **NoDeployment** a **ElementFile**.  
  
 Al importar receptores de eventos, el *Elements.xml* archivo se copia en la ubicación correcta, pero debe incluir manualmente el ensamblado en el paquete de solución para que se implemente con la solución. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] Cómo hacer esto, consulte [Cómo: agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Al importar los flujos de trabajo, los formularios de InfoPath se copian en la carpeta **Otros archivos importados** . Si el *.wsp* archivo contiene una plantilla Web, se establece como la página de inicio en **el Explorador de soluciones**.  
  
## <a name="import-fields-and-property-bags"></a>Importar campos y contenedores de propiedades
 Al importar una solución que tiene varios campos, todas las definiciones de campo independientes se combinan en una sola *Elements.xml* archivo bajo un nodo en **el Explorador de soluciones** llamado **campos** . De forma similar, todas las entradas de la bolsa de propiedades se combinan en un *Elements.xml* archivo en un nodo denominado **PropertyBags**.  
  
 Los campos de SharePoint son columnas de un tipo de datos especificado, como texto, booleano o búsqueda. Para obtener más información, vea [Bloque de creación: columnas y tipos de campo](http://go.microsoft.com/fwlink/?LinkId=182304). Los contenedores de propiedades permiten agregar propiedades a los objetos de SharePoint, desde una granja de servidores a una lista en un sitio de SharePoint. Los contenedores de propiedades se implementan como una tabla hash de valores y nombres de propiedad. Para obtener más información, vea [Administrar la configuración de SharePoint](http://go.microsoft.com/fwlink/?LinkId=182296) o [Valores de bolsa de propiedades de SharePoint](http://go.microsoft.com/fwlink/?LinkId=182297).  
  
## <a name="delete-items-in-the-project"></a>Eliminar elementos del proyecto
 La mayoría de los elementos en las soluciones de SharePoint tienen uno o varios elementos dependientes. Por ejemplo, las instancias de lista dependen de los tipos de contenido y los tipos de contenido dependen de los campos. Después de importar una solución de SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no le informa de ningún problema de referencia si elimina un elemento de la solución, ni de sus elementos dependientes, hasta que intente implementar la solución. Por ejemplo, si una solución importada tiene una instancia de lista que depende de un tipo de contenido y elimina ese tipo de contenido, podría producirá un error en la implementación. El error se produce si el elemento dependiente no está presente en el servidor de SharePoint. De forma similar, si un elemento eliminado también tiene una bolsa de propiedades relacionada, elimine estas entradas de la bolsa de propiedades de la **PropertyBags** *Elements.xml* archivo. Por lo tanto, si elimina los elementos de una solución importada y obtiene errores de implementación, compruebe si es necesario eliminar también los elementos dependientes.  
  
## <a name="restore-missing-feature-attributes"></a>Restaurar los atributos que faltan
 Cuando se importan soluciones, algunos atributos de características opcionales se omiten en el manifiesto de la función importada. Si desea restaurar estos atributos en el nuevo archivo de característica, identifique los atributos que faltan comparando el archivo de la característica original con el nuevo manifiesto de característica y siga las instrucciones del tema [Cómo: personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>No se realiza la detección de conflictos de implementación en instancias de lista integradas
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] no realiza la detección de conflictos de implementación en instancias de lista integradas (es decir, las instancias de lista predeterminadas incluidas con SharePoint). No realizar la detección de conflictos se hace para evitar sobrescribir las instancias de lista integradas en SharePoint. La instancias de lista integradas se siguen implementando o actualizando, pero nunca se eliminan o sobrescriben. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Solución de problemas de empaquetado de SharePoint e implementación](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="import-sharepoint-server-2010-workflows"></a>Importar flujos de trabajo de SharePoint Server 2010
 Si importa un flujo de trabajo creado en [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], no se ejecutará correctamente después de implementarlo. El flujo de trabajo no se ejecuta correctamente porque faltan ciertos ensamblados y  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] flujos de trabajo contienen formularios de InfoPath que no se admiten actualmente en soluciones de flujo de trabajo de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Sin embargo, los flujos de trabajo de [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] importados pueden configurarse para que funcione correctamente después de corregir algunos elementos, como agregar referencias a los ensamblados [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] y volver a conectar los formularios de InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Importar flujos de trabajo de SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=182226).  
  
## <a name="item-name-character-limit"></a>Límite de caracteres del nombre de elemento
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tiene un límite de 260 caracteres totales por proyecto y nombre de elemento de proyecto, incluida la ruta de acceso. Al importar una solución, si un nombre de elemento supera este límite, se produce el error:  
  
 **La ruta de acceso especificada, el nombre de archivo o ambos son demasiado largos. El nombre de archivo completo debe ser inferior a 260 caracteres y el nombre del directorio debe ser inferior a 248**.  
  
 Cuando se obtiene este error, no se crea el elemento. Este problema se produce con más frecuencia con los módulos importados. Para evitar este problema, haga lo siguiente:  
  
-   Use nombres cortos para el proyecto cuando los escriba en el cuadro de diálogo **Agregar nuevo proyecto** .  
  
-   Cree el proyecto en una ubicación lo más cercana posible a la carpeta raíz, con el fin de acortar la ruta de acceso.  
  
## <a name="the-sharepointproductversion-attribute"></a>El atributo SharePointProductVersion
 Si importa una solución creada en una versión anterior de SharePoint como [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] o [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], cambie el valor del atributo SharePointProductVersion en el manifiesto del paquete a 12.0, o bien inserte un control de administrador de script en todas las páginas web importadas y deje SharePointProductVersion establecido en 14.0. De lo contrario, los formularios web importados no se mostrarán en SharePoint.  
  
### <a name="background"></a>Fondo  
 Las soluciones de [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] y [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] incluyen el atributo SharePointProductVersion. SharePoint usa este atributo en sus manifiestos de paquete para determinar la versión de SharePoint para la que está diseñada la solución. Los dos valores válidos son 12.0 y 14.0. Un valor de 12.0 indica que el elemento está diseñado para [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] o [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]; el valor 14.0 indica que el elemento está diseñado para [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] o [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 Para mejorar la seguridad al representar páginas ASPX, [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] y [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] requieren que todas las páginas maestras o ASPX contengan un control de administrador de la secuencia de comandos. Para obtener más información sobre el administrador de la secuencia de comandos, consulte [Información general del control ScriptManager](http://go.microsoft.com/fwlink/?LinkID=169399). Dado que el control del administrador de script no estaba disponible en [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] y [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], uno debe agregarse a cualquier página [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] o [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] actualizada a [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] o [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. Las páginas ASPX que utilizan una página maestra estándar no requieren un control de administrador de scripts porque ya se agrega a la página maestra estándar. Sin embargo, las páginas ASPX que no usan una página maestra o que usan una página maestra personalizada deben agregar un control de script para que funcionen en [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] o [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 La ausencia de un control de administrador de script puede ser un problema cuando se importa un proyecto de [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] o [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] en [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], porque el atributo SharePointProductVersion de todos los nuevos proyectos está establecido en 14.0. Si implementa un proyecto actualizado que tiene un formulario web sin administrador de scripts, el formulario no se mostrará en SharePoint.  
  
## <a name="see-also"></a>Vea también
 [Tutorial: Importar elementos de un sitio de SharePoint existente](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)   
 [Pautas para importar flujos de trabajo reutilizables](../sharepoint/guidelines-for-importing-reusable-workflows.md)   
 [Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)   
 [Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)  
