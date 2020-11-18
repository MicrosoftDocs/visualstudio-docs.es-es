---
title: 'Cómo: crear un receptor de eventos | Microsoft Docs'
description: Cree un receptor de eventos para que pueda responder cuando un usuario interactúe con elementos de SharePoint como listas o elementos de lista.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e94bd1594f94f43c82eed5033d6ec2660905c18
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849888"
---
# <a name="how-to-create-an-event-receiver"></a>Cómo: crear un receptor de eventos
  Al crear *receptores de eventos*, puede responder cuando un usuario interactúa con elementos de SharePoint como listas o elementos de lista. Por ejemplo, el código de un receptor de eventos se puede desencadenar cuando un usuario cambia el calendario o elimina un nombre de una lista de contactos. Siguiendo este tema, puede obtener información sobre cómo agregar un receptor de eventos a una instancia de lista.

 Para completar estos pasos, debe tener instaladas [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y las ediciones compatibles de Windows y SharePoint. Dado que este ejemplo requiere un proyecto de SharePoint, también debe haber completado el procedimiento en el tema [Tutorial: crear una columna de sitio, un tipo de contenido y una lista para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Adición de un receptor de eventos
 El proyecto que creó en [Tutorial: crear una columna de sitio, un tipo de contenido y una lista para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) incluye columnas de sitio personalizadas, una lista personalizada y un tipo de contenido. En el procedimiento siguiente, expanda este proyecto agregando un controlador de eventos simple (un receptor de eventos) a una instancia de lista para mostrar cómo controlar los eventos que se producen en elementos de SharePoint como listas.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Para agregar un receptor de eventos a la instancia de lista

1. Abra el proyecto que creó en [Tutorial: crear una columna de sitio, un tipo de contenido y una lista para SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2. En **Explorador de soluciones**, elija el nodo de proyecto de SharePoint, que se denomina **Clinic**.

3. En la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

4. En **Visual C#** o **Visual Basic**, expanda el nodo **SharePoint** y, a continuación, elija el elemento **2010** .

5. En el panel **plantillas** , elija **receptor de eventos**, asígnele el nombre **TestEventReceiver1** y, a continuación, elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** .

6. En la lista **¿Qué tipo de receptor de eventos desea?** , elija **eventos de elemento de lista**.

7. En la lista **¿qué elemento debe ser el origen del evento?** , elija **pacientes (Clinic\Patients)**.

8. En la lista **controlar los siguientes eventos** , active la casilla situada junto a **un elemento que se ha agregado** y, a continuación, elija el botón **Finalizar** .

     El archivo de código para el nuevo receptor de eventos contiene un solo método denominado `ItemAdded` . En el paso siguiente, agregará código a este método para que todos los contactos se llamen de forma predeterminada a Scott Brown.

9. Reemplace el `ItemAdded` método existente por el código siguiente y, a continuación, elija la tecla **F5** :

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     El código se ejecuta y el sitio de SharePoint aparece en el explorador Web.

10. En la barra de inicio rápido, elija el vínculo **pacientes** y, a continuación, elija el vínculo **Agregar nuevo elemento** .

     Se abre el formulario de entrada de nuevos elementos.

11. Escriba los datos en los campos y, a continuación, elija el botón **Guardar** .

     Después de elegir el botón **Guardar** , la columna **patient Name** se actualiza automáticamente al nombre Scott Brown.

## <a name="see-also"></a>Consulte también

- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)