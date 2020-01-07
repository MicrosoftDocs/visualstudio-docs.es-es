---
title: 'Diseñador de flujo de trabajo: System. Activities, elegir elementos del cuadro de herramientas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f1a7030b6c351407814314ccd41e0e2ed6a880e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593114"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System. Activities (pestaña), elegir elementos del cuadro de herramientas (cuadro de diálogo)

Esta pestaña del cuadro de diálogo **elegir elementos del cuadro de herramientas** muestra una lista de actividades Windows Workflow Foundation (WF), plantillas y elementos disponibles. Para mostrar esta lista, seleccione **elegir elementos del cuadro de herramientas** en el menú **herramientas** o haga clic con el botón secundario en el cuadro de **herramientas** y seleccione **elegir elementos** para mostrar el cuadro de diálogo **elegir elementos del cuadro de herramientas** y, a continuación, seleccione la pestaña **System.** Activities. Core. Presentation, que contiene actividades de flujo de trabajo. sin embargo, solo se activan de forma predeterminada las actividades proporcionadas por el sistema y las actividades agregadas a través de otros ensamblados que se muestran en el **cuadro de herramientas** . Las actividades agregadas recientemente se comprueban automáticamente y aparecen en el cuadro de **herramientas** al hacer clic en **Aceptar** en el cuadro de diálogo. Además, estos elementos aparecen en el **cuadro de herramientas** en una nueva categoría que corresponde al espacio de nombres en el que reside la actividad, el elemento o la plantilla.

> [!WARNING]
> Si intenta agregar un ensamblado que no contenga actividades de flujo de trabajo, aparecerá un diálogo de error que indica que el ensamblado no contiene ninguna actividad.

Este cuadro de diálogo es independiente del proyecto y, por tanto, la pestaña **System. Activities** sigue mostrándose en XAML independiente o en un tipo de proyecto que no es de flujo de trabajo.

El filtrado se realiza en cada pestaña y no es posible agregar actividades de flujo de trabajo a través de la pestaña del **componente .net** . Agréguelos a través de la propia pestaña **System. Activities** .

Puede desproteger los elementos que no desee ver en el **cuadro de herramientas** de esta pestaña del cuadro de diálogo, o bien, puede hacerlo mediante la opción **eliminar** clic con el botón secundario en el **cuadro de herramientas** y la desreferenciación de un ensamblado no quita el elemento del cuadro de **herramientas**.

Al crear instancias de la actividad, para lo cual se debe arrastrar y colocar en el diseñador, se agrega automáticamente el ensamblado que contiene el elemento a la lista de ensamblados a la que se hace referencia. También si la actividad hace referencia a un ensamblado C, no agrega C a la lista de ensamblados a la que se hace referencia. El ensamblado C tiene que estar en la GAC o en el mismo directorio que la actividad B. En el caso independiente, el ensamblado tiene que estar en la GAC o en las rutas de acceso de sondeo de VS. A continuación solo puede arrastrar y colocar la actividad en la superficie del diseñador de flujo de trabajo.

La configuración del **cuadro de herramientas** se guarda de forma predeterminada como opciones de usuario, por lo que la próxima vez que abra el **cuadro de herramientas**, se mostrará la lista personalizada de actividades de flujo de trabajo. Un efecto secundario de esto es que si ha agregado los elementos de dominio específicos al cuadro de **herramientas** a través del cuadro de diálogo **elegir elementos del cuadro de herramientas** , sigue viendo esos elementos al trabajar en una aplicación de consola de flujos de trabajo. Si no desea verlos, elimínelos mediante el menú contextual o desactive las opciones en el cuadro de diálogo **elegir elementos del cuadro de herramientas** como se indicó anteriormente.

Las columnas en este cuadro de diálogo contienen la siguiente información:

Name\
Ofrece una lista de los nombres de las actividades de flujo de trabajo que están registradas en esos momentos en el equipo local.

System.IO
Muestra la jerarquía del espacio de nombres de .NET que define la estructura de la actividad.

Nombre de ensamblado\
Muestra el nombre y la versión del ensamblado .NET que contiene la actividad.

Active
Muestra la ubicación del ensamblado .NET que contiene las actividades de flujo de trabajo. La ubicación predeterminada de todos los ensamblados es la caché global de ensamblados.

Para ordenar los componentes de la lista, seleccione cualquier encabezado de columna.
