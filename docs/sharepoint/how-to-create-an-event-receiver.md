---
title: 'Cómo: crear un receptor de eventos | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd4528a47215254684be51400329b05c3998bbab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42635153"
---
# <a name="how-to-create-an-event-receiver"></a>Cómo: crear un receptor de eventos
  Creando *receptores de eventos*, puede responder cuando un usuario interactúa con los elementos de SharePoint como listas o elementos de lista. Por ejemplo, el código en un receptor de eventos se activan cuando un usuario cambia el calendario o elimina un nombre de una lista de contactos. Siguiendo este tema, aprenderá cómo agregar un receptor de eventos a una instancia de lista.

 Para completar estos pasos, debe tener instalado [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y ediciones compatibles de Windows y SharePoint. Dado que este ejemplo requiere un proyecto de SharePoint, también debe haber completado el procedimiento descrito en el tema [Tutorial: crear una columna de sitio, el tipo de contenido y la lista de SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

## <a name="adding-an-event-receiver"></a>Agregar un receptor de eventos
 El proyecto que creó en [Tutorial: crear una columna de sitio, el tipo de contenido y la lista de SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) incluye columnas de sitio personalizadas, una lista personalizada y un tipo de contenido. En el siguiente procedimiento, deberá expandir este proyecto mediante la adición de un controlador de eventos sencillo (un receptor de eventos) a una instancia de lista para mostrar cómo controlar eventos que se producen en los elementos de SharePoint como listas.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Para agregar un receptor de eventos a la instancia de lista

1.  Abra el proyecto que creó en [Tutorial: crear una columna de sitio, el tipo de contenido y la lista de SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).

2.  En **el Explorador de soluciones**, elija el nodo de proyecto de SharePoint, que se denomina **Clinic**.

3.  En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

4.  Bajo **Visual C#** o **Visual Basic**, expanda el **SharePoint** nodo y, a continuación, elija el **2010** elemento.

5.  En el **plantillas** panel, elija **receptor de eventos**, asígnele el nombre **TestEventReceiver1**y, a continuación, elija el **Aceptar** botón.

     El **Asistente de personalización de SharePoint** aparece.

6.  En el **qué tipo de receptor de eventos desea?** elija **eventos del elemento de lista**.

7.  En el **qué elemento debe ser el origen del evento?** elija **pacientes (Clinic\Patients)**.

8.  En el **administrar los eventos siguientes** lista, active la casilla situada junto a **se agregó un elemento**y, a continuación, elija el **finalizar** botón.

     El archivo de código para el nuevo receptor de eventos contiene un único método que se denomina `ItemAdded`. En el paso siguiente, agregará código a este método para que se llamará a cada contacto Scott Brown de forma predeterminada.

9. Reemplazar existente `ItemAdded` método con el siguiente código y, a continuación, elija el **F5** clave:

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     El código se ejecuta y el sitio aparece en el explorador web de SharePoint.

10. En la barra Inicio rápido, elija el **pacientes** vincular y, a continuación, elija el **Agregar nuevo elemento** vínculo.

     Se abre el formulario de entrada para los nuevos elementos.

11. Escriba datos en los campos y, a continuación, elija el **guardar** botón.

     Después de elegir la **guardar** botón, el **nombre paciente** columna se actualiza automáticamente al nombre Scott Brown.

## <a name="see-also"></a>Vea también

- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)