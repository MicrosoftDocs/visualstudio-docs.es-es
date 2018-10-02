---
title: Vincular elementos de modelo y los elementos de trabajo | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 603438fda4c2f883376292b68896309a4e669be5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580307"
---
# <a name="link-model-elements-and-work-items"></a>Vincular elementos de modelo con elementos de trabajo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [vincular elementos de modelo y los elementos de trabajo](https://docs.microsoft.com/visualstudio/modeling/link-model-elements-and-work-items).  
  
Para realizar el seguimiento de tareas, casos de prueba, errores, requisitos, problemas y otros trabajos relacionados con el modelo, vincule los elementos del modelo en Visual Studio y los elementos de trabajo en Team Foundation Server o Visual Studio Team Services. Asocie documentos a elementos de trabajo vinculados para asociarlos a los elementos del modelo.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  Debe usar Team Explorer para crear y abrir los vínculos. Asegúrese de que el proyecto de modelado y los diagramas se protegen en el control de versiones para que otros puedan abrir los diagramas vinculados.  
  
 Puede vincular, por ejemplo:  
  
-   Un elemento de trabajo de caso de usuario y un diagrama de actividades para mostrar cómo llevar a cabo el caso como una secuencia de operaciones.  
  
-   Un caso de uso de un diagrama de casos de uso y los elementos de trabajo de caso de prueba para asegurarse de que el caso de uso se implementa correctamente.  
  
-   Un atributo de una clase de un diagrama de clases UML y un elemento de trabajo de error para mostrar un error en la implementación del atributo.  
  
-   Un componente de un diagrama de componentes y un elemento de trabajo de tarea para realizar el seguimiento del desarrollo del componente. Este tipo de tarea generalmente se desglosa en otras más pequeñas.  
  
 Puede vincular elementos de trabajo a cualquiera de los elementos que se pueden seleccionar en los diagramas de modelado o en el Explorador de modelos UML, como estos elementos.  
  
-   Todos los elementos de los modelos UML, como las clases UML, las líneas de vida, los casos de uso, los subsistemas, las actividades, los nodos de objeto, los componentes y las interfaces  
  
-   Todas las relaciones de los modelos UML, como las asociaciones, las generalizaciones, las dependencias, los flujos y los mensajes  
  
-   Partes de los elementos, como los atributos y las operaciones de clases, las incidencias de ejecución de líneas de vida, los terminales de entrada y salida de las actividades y los elementos y puertos de los componentes  
  
-   Capas y dependencias de las capas  
  
-   Comentarios y vínculos de comentarios  
  
-   Diagramas. Para seleccionar un diagrama, elija una parte en blanco del diagrama.  
  
> [!WARNING]
>  Ya debe estar conectado al control de código fuente TFS (SCC) para crear o vincular a un elemento de trabajo. Si intenta abrir una conexión a un SCC TFS diferente, Visual Studio cierra automáticamente la solución actual. Asegúrese de que ya está conectado al SCC apropiado antes de intentar crear o vincular a un elemento de trabajo. En las versiones posteriores de Visual Studio, los comandos de menú no están disponibles si no está conectado a un SCC.  
  
-   [Conectarse a un proyecto de equipo](#ConnectTFS)  
  
-   [Vincular un elemento del modelo a un nuevo elemento de trabajo](#LinkNew)  
  
-   [Vincular un elemento del modelo a un elemento de trabajo existente](#LinkExisting)  
  
-   [Ver elementos de trabajo vinculados a un elemento de modelo](#OpenWorkItem)  
  
-   [Ver elementos de modelo vinculados a un elemento de trabajo](#ViewLinkedModels)  
  
-   [Eliminar los vínculos entre elementos del modelo y los elementos de trabajo](#RemoveLinks)  
  
-   [Solución de problemas](#Troubleshooting)  
  
##  <a name="ConnectTFS"></a> Conectarse a un proyecto de equipo  
 Para crear, ver o quitar vínculos, primero debe conectarse a su proyecto de equipo.  
  
1.  En el menú **Equipo** , elija **Administrar conexiones** para mostrar la ventana de Team Explorer.  
  
2.  Si no aparece el proyecto correcto, elija **Administrar conexiones** en Team Explorer y luego **Conectar al proyecto de equipo**. A continuación, elija los proyectos correctos, o el servidor si es necesario.  
  
3.  En **Team Explorer**, elija el proyecto donde desea crear, vincular o ver elementos de trabajo.  
  
##  <a name="LinkNew"></a> Vincular un elemento del modelo a un nuevo elemento de trabajo  
  
1.  Asegúrese de que está conectado a la instancia TFS que quiere utilizar.  
  
2.  En el diagrama de modelado o en el **Explorador de modelos UML**, abra el menú contextual del elemento de modelo.  
  
3.  Elija **Crear elemento de trabajo** y la clase de elemento de trabajo que desea crear.  
  
4.  Rellene los campos del formulario del elemento de trabajo. Elija **Guardar elemento de trabajo**.  
  
     Visual Studio vincula el elemento de modelo al nuevo elemento de trabajo. Un icono aparece en elemento del modelo o cerca de él.  
  
> [!WARNING]
>  Ya debe estar conectado al control de código fuente TFS (SCC) para crear o vincular a un elemento de trabajo. Si intenta abrir una conexión a un SCC TFS diferente, Visual Studio cierra automáticamente la solución actual. Asegúrese de que ya está conectado al SCC apropiado antes de intentar crear o vincular a un elemento de trabajo. En las versiones posteriores de Visual Studio, los comandos de menú no están disponibles si no está conectado a un SCC.  
  
##  <a name="LinkExisting"></a> Vincular un elemento del modelo a un elemento de trabajo existente  
 Cuando enlace elementos de modelo a elementos de trabajo, empiece por el elemento de modelo, no por el elemento de trabajo.  
  
1.  Asegúrese de que está conectado a la instancia TFS que quiere utilizar.  
  
2.  En el diagrama de modelado o en el **Explorador de modelos UML**, abra el menú contextual del elemento de modelo. Elija **Vincular a elemento de trabajo**. A continuación, seleccione el proyecto en el campo **Proyecto** .  
  
3.  Elija uno o varios elementos de trabajo para vincularlos al elemento de modelo mediante uno de los siguientes pasos:  
  
    -   Elija una consulta en **Consulta guardada**.  
  
    -   Escriba los identificadores de uno o varios elementos de trabajo separados mediante espacios, en **Identificadores**.  
  
    -   Escriba una palabra o frase en **El título contiene**.  
  
4.  Elija **Buscar**.  
  
5.  En la lista de elementos de trabajo, seleccione el elemento o elementos de trabajo que desee vincular.  
  
     Cuando haya terminado, la propiedad **Elementos de trabajo** del elemento del modelo mostrará un número mayor que el anterior. También aparecerá un icono en el elemento del modelo o cerca del mismo.  
  
> [!WARNING]
>  Ya debe estar conectado al control de código fuente TFS (SCC) para crear o vincular a un elemento de trabajo. Si intenta abrir una conexión a un SCC TFS diferente, Visual Studio cierra automáticamente la solución actual. Asegúrese de que ya está conectado al SCC apropiado antes de intentar crear o vincular a un elemento de trabajo. En las versiones posteriores de Visual Studio, los comandos de menú no están disponibles si no está conectado a un SCC.  
  
##  <a name="OpenWorkItem"></a> Ver elementos de trabajo vinculados a un elemento de modelo  
  
1.  En **Team Explorer**, asegúrese de que esté conectado al proyecto de equipo en el que están vinculados los elementos de trabajo al elemento de modelo.  
  
2.  En el diagrama de modelado o en el **Explorador de modelos UML**, abra el menú contextual del elemento de modelo. Elija **Ver elementos de trabajo** para ver la lista de elementos de trabajo vinculados.  
  
    > [!NOTE]
    >  Solo aparecerán los elementos de trabajo del servidor actualmente conectado. Si no ve ningún elemento de trabajo, asegúrese de que está conectado al servidor correcto en **Team Explorer**.  
  
##  <a name="ViewLinkedModels"></a> Ver elementos de modelo vinculados a un elemento de trabajo  
 Puede ver los elementos y los diagramas de modelado vinculados a un elemento de trabajo en Visual Studio Team Services y en Team Foundation Server 2012 o posterior. Por ejemplo, un elemento de trabajo se puede vincular a modelos de clases que muestren el diseño de las nuevas clases que se van a implementar.  
  
1.  En **Team Explorer**, asegúrese de que esté conectado al proyecto de equipo en el que están vinculados los elementos de modelo al elemento de trabajo.  
  
    > [!NOTE]
    >  Puede utilizar Team Explorer, no Team Web Access, para ver los elementos del modelo vinculados. Asegúrese de que el área de trabajo está asignada al proyecto de modelado que contiene los diagramas o elementos de modelado. Si no cuenta con un área de trabajo, debe crearla. Consulte [Troubleshooting](#Troubleshooting) y [crear y trabajar con áreas de trabajo](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).  
  
2.  Abra el elemento de trabajo y elija **Vínculos**. En **Vínculo de modelo**, abra el menú contextual del elemento de modelo vinculado. Elija **Abrir elemento vinculado**.  
  
     ![Elemento de modelo vinculado abierto de un elemento de trabajo](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")  
  
##  <a name="RemoveLinks"></a> Eliminar los vínculos entre elementos del modelo y los elementos de trabajo  
 Para quitar un elemento de trabajo vinculado, empiece por el elemento del modelo. De este modo se quita correctamente el vínculo recíproco entre ese elemento de modelo y el elemento de trabajo. Si comienza por el elemento de trabajo, el vínculo recíproco del elemento de modelo al elemento de trabajo no se eliminará.  
  
1.  En el diagrama de modelado o en el **Explorador de modelos UML**, abra el menú contextual del elemento de modelo.  
  
2.  Elija **Quitar elementos de trabajo**.  
  
     \- o -  
  
    1.  Elija **Propiedades**y, después, **Elementos de trabajo** , donde aparece el número de elementos de trabajo vinculados.  
  
    2.  En la propiedad **Elementos de trabajo** , elija el botón de puntos suspensivos **[…]**.  
  
        > [!NOTE]
        >  Solo aparecen los elementos de trabajo del servidor actual. Si la lista está vacía pero el número de elementos de trabajo no es cero, asegúrese de que la conexión se ha establecido con el servidor correcto en **Team Explorer**.  
  
3.  En **Quitar vínculos a elementos de trabajo**, desactive los elementos seleccionados que desea desvincular. Elija **Aceptar**.  
  
##  <a name="Troubleshooting"></a> Solución de problemas  
  
|**Problema**|**Causa posible**|**Resolución**|  
|---------------|------------------------|--------------------|  
|No se encuentra el elemento de modelo que desea vincular.|El elemento podría estar en un diagrama de un proyecto de modelado que se encuentra en [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Podría no tener ningún área de trabajo asignada al diagrama.|Asigne el área de trabajo al proyecto de modelado y al diagrama. Si no cuenta con un área de trabajo, debe crearla.<br /><br /> El mensaje de error que aparece para este problema contiene la ruta de acceso que puede usar para asignar el área de trabajo.<br /><br /> Consulte [crear y trabajar con áreas de trabajo](http://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|  
|No se encuentra el elemento de modelo vinculado.|El elemento vinculado podría estar en un diagrama que se ha movido o eliminado, o cuyo nombre ha cambiado.|1.  En el elemento de trabajo, elimine el vínculo al elemento de modelo.<br />2.  Cree un nuevo vínculo a partir del elemento de trabajo al elemento de modelo.|  
|El elemento de trabajo no tiene los elementos de modelo vinculados que esperaba.|Un elemento de trabajo muestra un elemento de capa vinculado solo si el vínculo se creó desde el elemento de trabajo. Si su equipo no usa [!INCLUDE[esprscc](../includes/esprscc-md.md)], se usará la ruta de acceso local de los diagramas para crear los vínculos. Si el proyecto de modelado y sus diagramas están en [!INCLUDE[esprscc](../includes/esprscc-md.md)], todos los miembros del equipo que tengan acceso al proyecto pueden ver los elementos vinculados en los elementos de trabajo.|Intente actualizar el elemento de trabajo.|  
|Al eliminar un vínculo a un elemento de modelo desde un elemento de trabajo, el vínculo del elemento de modelo al elemento de trabajo no se elimina.||Elimine el vínculo al elemento de trabajo a partir del elemento de modelo.|  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)



