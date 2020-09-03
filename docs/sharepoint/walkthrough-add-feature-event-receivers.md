---
title: 'Tutorial: agregar receptores de eventos de características | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f40358c157ec24557947f36b0c6eadb6d8a2622d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015366"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Tutorial: agregar receptores de eventos de características
  Los receptores de eventos de características son métodos que se ejecutan cuando se produce uno de los siguientes eventos relacionados con características en SharePoint:

- Se instala una característica.

- Una característica está activada.

- Una característica está desactivada.

- Se quita una característica.

  En este tutorial se muestra cómo agregar un receptor de eventos a una característica en un proyecto de SharePoint. Muestra las tareas siguientes:

- Crear un proyecto vacío con un receptor de eventos de características.

- Controlar el método **FeatureDeactivating** .

- Usar el modelo de objetos de proyecto de SharePoint para agregar un anuncio a la lista de anuncios.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- Ediciones compatibles de Microsoft Windows y SharePoint.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>Crear un proyecto de receptor de eventos de características
 En primer lugar, cree un proyecto para que contenga el receptor de eventos de características.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Para crear un proyecto con un receptor de eventos de características

1. En la barra de menús, elija **archivo**  >  **nuevo**  >  **proyecto** para mostrar el cuadro de diálogo **nuevo proyecto** .

2. Expanda el nodo **SharePoint** en **Visual C#** o **Visual Basic**y, a continuación, elija el nodo **2010** .

3. En el panel **plantillas** , elija la plantilla de **proyecto de SharePoint 2010** .

     Este tipo de proyecto se usa para los receptores de eventos de características porque no tienen ninguna plantilla de proyecto.

4. En el cuadro **nombre** , escriba **FeatureEvtTest**y, a continuación, elija el botón **Aceptar** para mostrar el Asistente para la **Personalización de SharePoint**.

5. En la página **especifique el sitio y el nivel de seguridad de la depuración** , escriba la dirección URL del sitio del servidor de SharePoint al que desea agregar el nuevo elemento de campo personalizado o use la ubicación predeterminada (http:// \<*system name*> /).

6. En la sección **¿cuál es el nivel de confianza de esta solución de SharePoint?** , elija el botón de opción **implementar como solución de granja de servidores** .

     Para obtener más información sobre las soluciones en espacio aislado frente a las soluciones de granja, consulte [consideraciones sobre soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

7. Elija el botón **Finalizar** y observe que una característica denominada Feature1 aparece bajo el nodo **características** .

## <a name="add-an-event-receiver-to-the-feature"></a>Adición de un receptor de eventos a la característica
 Después, agregue un receptor de eventos a la característica y agregue el código que se ejecuta cuando se desactiva la característica.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>Para agregar un receptor de eventos a la característica

1. Abra el menú contextual del nodo características y, a continuación, elija **Agregar característica** para crear una característica.

2. En el nodo **características** , abra el menú contextual de **Feature1**y, a continuación, elija **Agregar receptor de eventos** para agregar un receptor de eventos a la característica.

     Esto agrega un archivo de código en Feature1. En este caso, se denomina *Feature1.EventReceiver.CS* o *Feature1. EventReceiver. VB*, dependiendo del lenguaje de desarrollo del proyecto.

3. Si el proyecto está escrito en [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] , agregue el código siguiente en la parte superior del receptor de eventos si aún no está ahí:

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. La clase del receptor de eventos contiene varios métodos con comentarios que actúan como eventos. Reemplace el método **FeatureDeactivating** por lo siguiente:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>Prueba del receptor de eventos de características
 A continuación, desactive la característica para probar si el método **FeatureDeactivating** envía un anuncio a la lista de anuncios de SharePoint.

#### <a name="to-test-the-feature-event-receiver"></a>Para probar el receptor de eventos de características

1. Establezca el valor de la propiedad de **configuración de implementación activa** del proyecto en **sin activación**.

     El establecimiento de esta propiedad evita que la característica se active en SharePoint y permite depurar receptores de eventos de características. Para obtener más información, vea [depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

2. Elija la tecla **F5** para ejecutar el proyecto e implementarlo en SharePoint.

3. En la parte superior de la Página Web de SharePoint, abra el menú **acciones del sitio** y, a continuación, elija **configuración del sitio**.

4. En la sección **acciones del sitio** de la página Configuración del **sitio** , elija el vínculo **administrar las características del sitio** .

5. En la página **características** , elija el botón **Activar** situado junto a la característica de **FeatureEvtTest Feature1** .

6. En la página **características** , elija el botón **desactivar** situado junto a la característica **FeatureEvtTest Feature1** y, a continuación, elija el vínculo **desactivar esta característica** para desactivar la característica.

7. Elija el botón **Inicio** .

     Observe que aparece un anuncio en la lista **anuncios** después de desactivar la característica.

## <a name="see-also"></a>Consulte también

- [Cómo: crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)