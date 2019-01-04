---
title: Diseñador de flujo de trabajo - pestaña System.Activities, elija el cuadro de diálogo de elementos de cuadro de herramientas
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de80c4def42febcc7029654ef22cfbab28a3796a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868188"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities (pestaña), Elegir elementos del cuadro de herramientas (cuadro de diálogo)

Esta pestaña de la **elegir elementos del cuadro de herramientas** cuadro de diálogo muestra una lista de actividades de Windows Workflow Foundation (WF), plantillas y elementos disponibles para usted. Para mostrar esta lista, seleccione **elegir elementos del cuadro de herramientas** desde el **herramientas** menús o haciendo clic con el **cuadro de herramientas** y seleccionando **elegir elementos**para mostrar el **elegir elementos del cuadro de herramientas** cuadro de diálogo y, a continuación, seleccione su **System.Activities** ficha. De fábrica, la lista contiene las actividades de flujo de trabajo desde ensamblados System.Activities, System.ServiceModel.Activities y System.Activities.Core.Presentation; Sin embargo, solo proporcionado por el sistema actividades que se muestran y las actividades agregadas a través de otros ensamblados que aparecen en la **cuadro de herramientas** están activadas de forma predeterminada. Recientemente agregó las actividades se comprueban automáticamente y aparecen en la **cuadro de herramientas** al hacer clic en **Aceptar** en el cuadro de diálogo. Además, estos elementos aparecen en la **cuadro de herramientas** en una nueva categoría que corresponde al espacio de nombres donde reside la actividad/elemento/plantilla.

> [!WARNING]
> Si intenta agregar un ensamblado que no contenga actividades de flujo de trabajo, aparecerá un diálogo de error que indica que el ensamblado no contiene ninguna actividad.

 Este cuadro de diálogo es independiente del proyecto y, por tanto, el **System.Activities** ficha sigue presentándose en XAML independiente o un tipo de proyecto sin flujo de trabajo.

 El filtrado se efectúa en cada pestaña. Esto significa que no es posible agregar actividades de flujo de trabajo a través de la **componente .NET** ficha. Tienen que agregarse a través de la **System.Activities** propia pestaña.

 Puede desactivar los elementos que no desea ver en el **cuadro de herramientas** desde este cuadro de diálogo tabulador, o como alternativa, puede hacerlo mediante el **eliminar** opción del menú contextual en el **cuadro de herramientas** y anulando las referencias a un ensamblado no quitan el elemento de la **cuadro de herramientas**.

 Al crear instancias de la actividad, para lo cual se debe arrastrar y colocar en el diseñador, se agrega automáticamente el ensamblado que contiene el elemento a la lista de ensamblados a la que se hace referencia. También si la actividad hace referencia a un ensamblado C, no agrega C a la lista de ensamblados a la que se hace referencia. Ensamblado C tiene que estar en la GAC o en el mismo directorio que la actividad B. En el caso independiente, el ensamblado debe estar en la GAC o las rutas de acceso de sondeo de VS. A continuación solo puede arrastrar y colocar la actividad en la superficie del diseñador de flujo de trabajo.

 **Cuadro de herramientas** configuración se guarda de forma predeterminada como opciones de usuario, por lo que la próxima vez, cuando se abre el **cuadro de herramientas**, muestra su lista personalizada de actividades de flujo de trabajo. Un efecto secundario de esto es que si ha agregado sus elementos específicos de dominio a la **cuadro de herramientas** a través de la **elegir elementos del cuadro de herramientas** cuadro de diálogo, seguirá viendo esos elementos cuando se trabaja un Flujo de trabajo también la aplicación de consola. Si no desea verlos, elimínelos mediante el menú contextual o anule su selección a través de la **elegir elementos del cuadro de herramientas** cuadro de diálogo como se indicó anteriormente.

 Las columnas en este cuadro de diálogo contienen la siguiente información:

 Name

 Ofrece una lista de los nombres de las actividades de flujo de trabajo que están registradas en esos momentos en el equipo local.

 Espacio de nombres

 Muestra la jerarquía del espacio de nombres de la biblioteca de clases de .NET Framework que define la estructura de la actividad.

 Nombre del ensamblado

 Muestra el nombre y versión del ensamblado de .NET Framework que contiene la actividad.

 Directorio

 Muestra la ubicación del ensamblado de .NET Framework que contiene las actividades de flujo de trabajo. La ubicación predeterminada de todos los ensamblados es la caché global de ensamblados.

 Para ordenar los componentes de la lista, seleccione cualquier encabezado de columna.