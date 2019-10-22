---
title: System. Activities (pestaña), elegir elementos del cuadro de herramientas (cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95b2aa636b63523e06e3c931381e4506a0a03bac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655170"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities (pestaña), Elegir elementos del cuadro de herramientas (cuadro de diálogo)
Esta pestaña del cuadro de diálogo **elegir elementos del cuadro de herramientas** muestra una lista de actividades [!INCLUDE[wf](../includes/wf-md.md)], plantillas y elementos disponibles. Para mostrar esta lista, seleccione **elegir elementos del cuadro de herramientas** en el menú **herramientas** o haga clic con el botón secundario en el cuadro de **herramientas** y seleccione **elegir elementos** para mostrar el cuadro de diálogo **elegir elementos del cuadro de herramientas** y, después, seleccione su  **Pestaña System. Activities** . de un equipo, la lista contiene actividades de flujo de trabajo de los ensamblados System. Activities, System. ServiceModel. Activities y System. Activities. Core. Presentation; sin embargo, solo se activan de forma predeterminada las actividades proporcionadas por el sistema y las actividades agregadas a través de otros ensamblados que se muestran en el **cuadro de herramientas** . Las actividades agregadas recientemente se comprueban automáticamente y aparecen en el cuadro de **herramientas** al hacer clic en **Aceptar** en el cuadro de diálogo. Además, estos elementos aparecen en el **cuadro de herramientas** en una nueva categoría que corresponde al espacio de nombres en el que reside la actividad, el elemento o la plantilla.

> [!WARNING]
> Si intenta agregar un ensamblado que no contenga actividades de flujo de trabajo, aparecerá un diálogo de error que indica que el ensamblado no contiene ninguna actividad.

 Este cuadro de diálogo es independiente del proyecto y, por tanto, la pestaña **System. Activities** sigue mostrándose en XAML independiente o en un tipo de proyecto que no es de flujo de trabajo.

 El filtrado se realiza en cada pestaña. Esto significa que no es posible agregar actividades de flujo de trabajo a través de la pestaña del **componente .net** . Tienen que agregarse a través de la propia pestaña **System. Activities** .

 Puede desproteger los elementos que no desee ver en el **cuadro de herramientas** de esta pestaña de diálogo, o bien, puede hacerlo mediante la opción de menú contextual **eliminar** del cuadro de **herramientas** y desreferenciar un ensamblado no quita el elemento de la  **Cuadro de herramientas**.

 Al crear instancias de la actividad, para lo cual se debe arrastrar y colocar en el diseñador, se agrega automáticamente el ensamblado que contiene el elemento a la lista de ensamblados a la que se hace referencia. También si la actividad hace referencia a un ensamblado C, no agrega C a la lista de ensamblados a la que se hace referencia. El ensamblado C tiene que estar en la GAC o en el mismo directorio que la actividad B. En el caso independiente, el ensamblado tiene que estar en la GAC o en las rutas de acceso de sondeo de VS. A continuación solo puede arrastrar y colocar la actividad en la superficie del diseñador de flujo de trabajo.

 La configuración del **cuadro de herramientas** se guarda de forma predeterminada como opciones de usuario, por lo que la próxima vez que abra el **cuadro de herramientas**, se mostrará la lista personalizada de actividades de flujo de trabajo. Un efecto secundario de esto es que si ha agregado los elementos de dominio específicos al cuadro de **herramientas** a través del cuadro de diálogo **elegir elementos del cuadro de herramientas** , sigue viendo esos elementos al trabajar en una aplicación de consola de flujos de trabajo. Si no desea verlos, elimínelos mediante el menú contextual o desactive las opciones en el cuadro de diálogo **elegir elementos del cuadro de herramientas** como se indicó anteriormente.

 Las columnas en este cuadro de diálogo contienen la siguiente información:

 Nombre muestra los nombres de las actividades de flujo de trabajo actualmente registradas en el equipo local.

 Espacio de nombres muestra la jerarquía del espacio de nombres de la biblioteca de clases .NET Framework que define la estructura de la actividad.

 Nombre del ensamblado muestra el nombre y la versión del ensamblado .NET Framework que contiene la actividad.

 Directorio muestra la ubicación del ensamblado de .NET Framework que contiene las actividades de flujo de trabajo. La ubicación predeterminada de todos los ensamblados es la caché global de ensamblados.

 Para ordenar los componentes de la lista, seleccione cualquier encabezado de columna.