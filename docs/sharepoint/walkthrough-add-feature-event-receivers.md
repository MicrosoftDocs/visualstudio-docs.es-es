---
title: 'Tutorial: Agregar receptores de eventos de característica | Documentos de Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9701281ed6b6e84a3147d6fdeda9ce045fcb5305
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865299"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Tutorial: Agregar receptores de eventos de característica
  Receptores de eventos son métodos que se ejecutan cuando se produce uno de los siguientes eventos relacionados con la característica en SharePoint:

- Se instala una característica.

- Se activa una característica.

- Una característica está desactivada.

- Se quita una característica.

  Este tutorial muestra cómo agregar un receptor de eventos a una característica en un proyecto de SharePoint. Muestra las tareas siguientes:

- Crear un proyecto vacío con un receptor de eventos de característica.

- Controlar la **FeatureDeactivating** método.

- Usar el modelo de objetos de proyecto de SharePoint para agregar un anuncio a la lista de anuncios.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

-   Ediciones compatibles de Microsoft Windows y SharePoint.

-   Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Crear un proyecto de receptor de eventos de característica
 En primer lugar, cree un proyecto para que contenga el receptor de eventos de característica.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Para crear un proyecto con un receptor de eventos de característica

1.  En la barra de menús, elija **archivo** > **New** > **proyecto** para mostrar el **nuevo proyecto** cuadro de diálogo.

2.  Expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija el **2010** nodo.

3.  En el **plantillas** panel, elija el **proyecto de SharePoint 2010** plantilla.

     Use este tipo de proyecto para los receptores de eventos de característica porque no tienen ninguna plantilla de proyecto.

4.  En el **nombre** , escriba **FeatureEvtTest**y, a continuación, elija el **Aceptar** botón para mostrar el **Asistente de personalización de SharePoint**.

5.  En el **especificar el nivel de sitio y de seguridad para la depuración** página, escriba la dirección URL del sitio de SharePoint server a la que desea agregar el nuevo elemento de campo personalizado o usar la ubicación predeterminada (http://\<*sistema nombre*> /).

6.  En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, elija el **implementar como solución de granja de servidores** botón de opción.

     Para obtener más información acerca de las soluciones en espacio aislado frente a soluciones de granja, vea [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

7.  Elija la **finalizar** botón y, a continuación, tenga en cuenta que una característica denominada Característica1 aparece bajo el **características** nodo.

## <a name="add-an-event-receiver-to-the-feature"></a>Agregar un receptor de eventos a la característica
 A continuación, agregar un receptor de eventos a la característica y agregue el código que se ejecuta cuando se desactiva la característica.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Para agregar un receptor de eventos a la característica

1.  Abra el menú contextual del nodo características y, a continuación, elija **Agregar característica** para crear una función.

2.  En el **características** nodo, abra el menú contextual para **Feature1**y, a continuación, elija **agregar receptor de eventos** para agregar un receptor de eventos a la característica.

     Esto agrega un archivo de código bajo Característica1. En este caso, se denomina cualquiera *Feature1.EventReceiver.cs* o *Feature1.EventReceiver.vb*, en función de lenguaje de desarrollo del proyecto.

3.  Si el proyecto está escrito en [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], agregue el código siguiente en la parte superior del receptor de eventos si aún no está:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4.  La clase del receptor de eventos contiene varios métodos comentados que actúan como eventos. Reemplace el **FeatureDeactivating** método con lo siguiente:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Probar el receptor de eventos de característica
 A continuación, desactive la característica para probar si el **FeatureDeactivating** método envía un anuncio a la lista de anuncios de SharePoint.

#### <a name="to-test-the-feature-event-receiver"></a>Para probar el receptor de eventos de característica

1.  Establezca el valor del proyecto **Active Deployment Configuration** propiedad **sin activación**.

     Al establecer esta propiedad evita que la característica de activación en SharePoint y le permite depurar receptores de eventos de característica. Para obtener más información, consulte [soluciones de SharePoint depurar](../sharepoint/debugging-sharepoint-solutions.md).

2.  Elija la **F5** clave para ejecutar el proyecto e implementarlo en SharePoint.

3.  En la parte superior de la página Web de SharePoint, abra el **acciones del sitio** menú y, a continuación, elija **configuración del sitio**.

4.  En el **acciones del sitio** sección de la **configuración del sitio** página, elija el **administrar características del sitio** vínculo.

5.  En el **características** página, elija el **activar** situado junto a la **FeatureEvtTest Feature1** característica.

6.  En el **características** página, elija el **Deactivate** situado junto a la **FeatureEvtTest Feature1** característica y, a continuación, elija el **desactivar esta característica**  vínculo de confirmación para desactivar la característica.

7.  Elija la **inicio** botón.

     Observe que aparece un anuncio en el **anuncios** después de desactiva la característica de lista.

## <a name="see-also"></a>Vea también

- [Cómo: Crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)