---
title: 'Cómo: crear un receptor de eventos para una instancia de la lista específica | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 950eeec82d7b7c49f0bbd76b13114f80f023a6dd
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119507"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Cómo: crear un receptor de eventos para una instancia de la lista específica
  Un receptor de eventos de la instancia de lista responde a los eventos que ocurren en cualquier instancia de una definición de lista. Aunque la plantilla de receptor de eventos no se permite el establecimiento de destinos de una instancia de la lista específica, puede modificar un receptor de eventos que se limita a una definición de lista para responder a eventos en una instancia de la lista específica.  
  
 Para tener como destino una instancia de lista específica en el *Elements.xml* para el receptor de eventos, reemplace `ListTemplateId` con `ListUrl` y agregue la dirección URL de la instancia de lista.  
  
## <a name="create-a-list-instance-event-receiver"></a>Crear un receptor de eventos de la instancia de lista  
 Los pasos siguientes muestran cómo modificar un receptor de eventos de elemento de lista para responder sólo a eventos que se producen en una instancia de la lista de anuncios personalizados.  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Para modificar un receptor de eventos para responder a una instancia de la lista específica  
  
1.  En un explorador, abra el sitio de SharePoint.  
  
2.  En el panel de navegación, **enumera** vínculo.  
  
3.  En el **todo el contenido del sitio** página, elija el **crear** vínculo.  
  
4.  En el **crear** diálogo cuadro, elija el **anuncios** escriba, asigne el nombre del anuncio **TestAnnouncements**y, a continuación, elija la **crear**botón.  
  
5.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de receptor de eventos.  
  
6.  En el **qué tipo de receptor de eventos desea?** elija **eventos del elemento de lista**.  
  
    > [!NOTE]  
    >  También puede seleccionar cualquier otro tipo de receptor de eventos que establece el ámbito para una definición de lista, por ejemplo, **eventos de correo electrónico de lista** o **eventos de flujo de trabajo de lista**.  
  
7.  En el **qué elemento debe ser el origen del evento?** elija **anuncios**.  
  
8.  En el **administrar los eventos siguientes** lista, seleccione el **se va a agregar un elemento** casilla de verificación y, a continuación, elija el **finalizar** botón.  
  
9. En **el Explorador de soluciones**, bajo EventReceiver1, abra *Elements.xml*.  
  
     El receptor de eventos actualmente hace referencia a la definición de la lista de anuncios mediante la línea siguiente:  
  
    ```xml  
    <Receivers ListTemplateId="104">  
    ```  
  
     Cambie esta línea al texto siguiente:  
  
    ```xml  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     Esto indica que el receptor de eventos para responder sólo a eventos que se producen en el nuevo **TestAnnouncements** lista de anuncios que acaba de crear. Puede cambiar el `ListURL` atributo hacer referencia a cualquier instancia de lista en el servidor de SharePoint.  
  
10. Abra el archivo de código para el receptor de eventos y colocar un punto de interrupción en el método ItemAdding.  
  
11. Elija la **F5** clave para compilar y ejecutar la solución.  
  
12. En SharePoint, elija el **TestAnnouncements** vínculo en el panel de navegación.  
  
13. Elija la **Agregar nuevo anuncio** vínculo.  
  
14. Escriba un título para el anuncio y, a continuación, elija el **guardar** botón.  
  
     Tenga en cuenta que el punto de interrupción se visita cuando se agrega el nuevo elemento a la lista de anuncios personalizados.  
  
15. Elija la **F5** tecla para continuar.  
  
16. En el panel de navegación, elija el **enumera** vincular y, a continuación, elija el **anuncios** vínculo.  
  
17. Agregar un nuevo anuncio.  
  
     Tenga en cuenta que el receptor de eventos no se desencadena en el nuevo anuncio porque el receptor está configurado para responder sólo a eventos en la instancia de la lista de anuncio personalizado, **TestAnnouncements**.  
  
## <a name="see-also"></a>Vea también
 [Cómo: crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
