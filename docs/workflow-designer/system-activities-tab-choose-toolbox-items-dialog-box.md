---
title: "System.Activities (pesta&#241;a), Elegir elementos del cuadro de herramientas (cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS"
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS"
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# System.Activities (pesta&#241;a), Elegir elementos del cuadro de herramientas (cuadro de di&#225;logo)
Esta pestaña del cuadro de diálogo **Elegir elementos del cuadro de herramientas** muestra una lista de actividades, plantillas y elementos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que se encuentran disponibles.Para mostrar esta lista, seleccione **Elegir elementos del cuadro de herramientas** del menú **Herramientas** o haga clic con el botón secundario en **Cuadro de herramientas** y seleccione **Elegir elementos** con el fin de mostrar el cuadro de diálogo **Elegir elementos del cuadro de herramientas** y, a continuación, seleccione la pestaña **System.Activities**.Los elementos están listos para usar y la lista contiene actividades de flujo de trabajo de ensamblados System.Activities, System.ServiceModel.Activities y System.Activities.Core.Presentation; sin embargo, solo se comprueban de forma predeterminada las actividades proporcionadas por el sistema que se muestran y las actividades agregadas a través de otros ensamblados que aparecen en el **Cuadro de herramientas**.Las actividades agregadas recientemente se comprueban automáticamente y aparecen en el **Cuadro de herramientas** al hacer clic en **Aceptar** en el cuadro de diálogo.Asimismo, estos elementos aparecen en el **Cuadro de herramientas** en una nueva categoría que corresponde al espacio de nombres donde reside la actividad\/elemento\/plantilla.  
  
> [!WARNING]
>  Si intenta agregar un ensamblado que no contenga actividades de flujo de trabajo, aparecerá un diálogo de error que indica que el ensamblado no contiene ninguna actividad.  
  
 Este cuadro de diálogo es independiente del proyecto y por tanto la pestaña **System.Activities** sigue presentándose en XAML independiente o como un tipo de proyecto sin flujo de trabajo.  
  
 El filtrado se efectúa en cada pestaña.Esto significa que no es posible agregar actividades de flujo de trabajo a través de la pestaña **.NET Component**.Es preciso que se agreguen a través de la pestaña **System.Activities**.  
  
 Puede anular la selección de los elementos que no desee ver en el **Cuadro de herramientas** de esta pestaña del diálogo o, alternativamente, puede hacerlo mediante la opción de menú contextual **Eliminar** en el **Cuadro de herramientas** y si se desreferencia un ensamblado no se quita el elemento del **Cuadro de herramientas**.  
  
 Al crear instancias de la actividad, para lo cual se debe arrastrar y colocar en el diseñador, se agrega automáticamente el ensamblado que contiene el elemento a la lista de ensamblados a la que se hace referencia.También si la actividad hace referencia a un ensamblado C, no agrega C a la lista de ensamblados a la que se hace referencia.El ensamblado C tiene que estar en la GAC o en el mismo directorio que la actividad B.En el caso independiente, el ensamblado tiene que estar en la GAC o las rutas de acceso de sondeo de VS.A continuación solo puede arrastrar y colocar la actividad en la superficie del diseñador de flujo de trabajo.  
  
 De forma predeterminada, se guarda la configuración del **Cuadro de herramientas** como opciones de usuario, de forma que la próxima vez que se abra el **Cuadro de herramientas**, aparecerá su lista personalizada de actividades de flujo de trabajo.Un efecto secundario de esto es que si ha agregado sus elementos de dominio concretos al **Cuadro de herramientas** a través del cuadro de diálogo **Elegir elementos del cuadro de herramientas**, seguirá viendo esos elementos también cuando trabaje con una aplicación de consola de flujos de trabajo.Si no desea verlos, elimínelos utilizando el menú contextual o anule su selección a través del cuadro de diálogo **Elegir elementos del cuadro de herramientas** tal como se ha explicado anteriormente.  
  
 Las columnas en este cuadro de diálogo contienen la siguiente información:  
  
 Nombre  
 Ofrece una lista de los nombres de las actividades de flujo de trabajo que están registradas en esos momentos en el equipo local.  
  
 Espacio de nombres  
 Muestra la jerarquía del espacio de nombres de la biblioteca de clases de .NET Framework que define la estructura de la actividad.  
  
 Nombre del ensamblado  
 Muestra el nombre y versión del ensamblado de .NET Framework que contiene la actividad.  
  
 Directorio  
 Muestra la ubicación del ensamblado de .NET Framework que contiene las actividades de flujo de trabajo.La ubicación predeterminada de todos los ensamblados es la caché global de ensamblados.  
  
 Para ordenar los componentes de la lista, seleccione cualquier encabezado de columna.