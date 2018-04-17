---
title: 'Cómo: crear un receptor de eventos para una instancia de lista específica | Documentos de Microsoft'
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
ms.openlocfilehash: 4d6d01b9f9ed0db8588124b71c982b2d37aa86ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Cómo: Crear un receptor de eventos para una instancia de lista genérica
  Un receptor de eventos de la instancia de lista responde a los eventos que se producen en cualquier instancia de una definición de lista. Aunque la plantilla de receptor de eventos no permitir que los destinatarios de una instancia de lista genérica, puede modificar un receptor de eventos en el ámbito de una definición de lista para responder a eventos en una instancia de lista concreta.  
  
 Que tenga como destino una instancia de lista concreta, en el Elements.xml para el receptor de eventos, reemplace `ListTemplateId` con `ListUrl` y agregue la dirección URL de la instancia de lista.  
  
## <a name="creating-a-list-instance-event-receiver"></a>Crear un receptor de eventos de la instancia de lista  
 Los pasos siguientes muestran cómo modificar un receptor de eventos de elemento de lista para responder a los eventos que se producen en una instancia de la lista de anuncios personalizados.  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Para modificar un receptor de eventos para responder a una instancia de lista genérica  
  
1.  En un explorador, abra el sitio de SharePoint.  
  
2.  En el panel de navegación, **enumera** vínculo.  
  
3.  En el **todo el contenido del sitio** página, elija la **crear** vínculo.  
  
4.  En el **crear** diálogo cuadro, elija la **anuncios** type, nombre del anuncio **TestAnnouncements**y, a continuación, elija la **crear**botón.  
  
5.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de receptor de eventos.  
  
6.  En el **¿qué tipo de receptor de eventos desea?** elija **eventos de elementos de lista**.  
  
    > [!NOTE]  
    >  También puede seleccionar cualquier otro tipo de receptor de eventos que abarca a una definición de lista, por ejemplo, **eventos de correo electrónico de lista** o **eventos de flujo de trabajo de lista**.  
  
7.  En el **qué elemento debe ser el origen del evento?** elija **anuncios**.  
  
8.  En el **administrar los eventos siguientes** lista, seleccione la **se agrega un elemento** casilla de verificación y, a continuación, elija la **finalizar** botón.  
  
9. En **el Explorador de soluciones**, bajo EventReceiver1, abra Elements.xml.  
  
     El receptor de eventos actualmente hace referencia a la definición de lista de anuncios mediante la línea siguiente:  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     Cambie esta línea por el texto siguiente:  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     Esto indica que el receptor de eventos para responder a los eventos que se producen en el nuevo **TestAnnouncements** lista de anuncios que acaba de crear. Puede cambiar el `ListURL` atributo hacer referencia a cualquier instancia de lista en el servidor de SharePoint.  
  
10. Abra el archivo de código para el receptor de eventos y colocar un punto de interrupción en el método ItemAdding.  
  
11. Presione la tecla F5 para compilar y ejecutar la solución.  
  
12. En SharePoint, elija el **TestAnnouncements** vínculo en el panel de navegación.  
  
13. Elija la **Agregar nuevo anuncio** vínculo.  
  
14. Escriba un título para ver el anuncio y, a continuación, elija la **guardar** botón.  
  
     Tenga en cuenta que el punto de interrupción se alcanza cuando el nuevo elemento se agrega a la lista de anuncios personalizados.  
  
15. Presione la tecla F5 para reanudar.  
  
16. En el panel de navegación, elija la **enumera** vincular y, a continuación, elija la **anuncios** vínculo.  
  
17. Agregar un nuevo anuncio.  
  
     Tenga en cuenta que el receptor de eventos no se desencadena en el nuevo anuncio porque el receptor está configurado para responder sólo a los eventos de la instancia de la lista de anuncio personalizado, **TestAnnouncements**.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  