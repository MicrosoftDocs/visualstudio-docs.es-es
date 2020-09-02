---
title: 'Cómo: crear un receptor de eventos para una instancia de lista específica | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
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
ms.openlocfilehash: 54c384742afba3d5af7f08ee62a9ec56c7f1438c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016962"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Cómo: crear un receptor de eventos para una instancia de lista específica
  Un receptor de eventos de instancia de lista responde a los eventos que se producen en cualquier instancia de una definición de lista. Aunque la plantilla de receptor de eventos no habilita el destino de una instancia de lista específica, puede modificar un receptor de eventos cuyo ámbito es una definición de lista para responder a los eventos de una instancia de lista específica.

 Para establecer como destino una instancia de lista específica, en el *Elements.xml* del receptor de eventos, reemplace `ListTemplateId` por `ListUrl` y agregue la dirección URL de la instancia de lista.

## <a name="create-a-list-instance-event-receiver"></a>Crear un receptor de eventos de instancia de lista
 En los pasos siguientes se muestra cómo modificar un receptor de eventos de elemento de lista para responder solo a los eventos que se producen en una instancia de lista de anuncios personalizada.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Para modificar un receptor de eventos para responder a una instancia de lista específica

1. En un explorador, abra el sitio de SharePoint.

2. En el panel de navegación, **muestra** el vínculo.

3. En la página **todo el contenido del sitio** , elija el vínculo **crear** .

4. En el cuadro de diálogo **crear** , elija el tipo de **anuncio** , asigne al anuncio el nombre **TestAnnouncements**y, a continuación, elija el botón **crear** .

5. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , cree un proyecto de receptor de eventos.

6. En la lista **¿Qué tipo de receptor de eventos desea?** , elija **eventos de elemento de lista**.

    > [!NOTE]
    > También puede seleccionar cualquier otro tipo de receptor de eventos que alcance una definición de lista, por ejemplo, **enumerar eventos de correo electrónico** o **enumerar eventos de flujo de trabajo**.

7. En la lista **¿qué elemento debe ser el origen del evento?** , elija **anuncios**.

8. En la lista **controlar los siguientes eventos** , active la casilla **se está agregando un elemento** y, a continuación, elija el botón **Finalizar** .

9. En **Explorador de soluciones**, en EventReceiver1, Abra *Elements.xml*.

     El receptor de eventos hace referencia actualmente a la definición de lista de anuncios mediante la siguiente línea:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Cambie esta línea por el texto siguiente:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Esto indica al receptor de eventos que responda solo a los eventos que se producen en la nueva lista de anuncios de **TestAnnouncements** que acaba de crear. Puede cambiar el `ListURL` atributo para hacer referencia a cualquier instancia de lista en el servidor de SharePoint.

10. Abra el archivo de código para el receptor de eventos y coloque un punto de interrupción en el método ItemAdding.

11. Elija la tecla **F5** para compilar y ejecutar la solución.

12. En SharePoint, elija el vínculo **TestAnnouncements** en el panel de navegación.

13. Elija el vínculo **Agregar nuevo anuncio** .

14. Escriba un título para el anuncio y elija el botón **Guardar** .

     Observe que se alcanza el punto de interrupción cuando el nuevo elemento se agrega a la lista de anuncios personalizados.

15. Elija la tecla **F5** para reanudarla.

16. En el panel de navegación, elija el vínculo **listas** y, a continuación, elija el vínculo **anuncios** .

17. Agregue un nuevo anuncio.

     Tenga en cuenta que el receptor de eventos no se activa en el anuncio nuevo porque el receptor está configurado para responder solo a los eventos de la instancia de lista de anuncios personalizada, **TestAnnouncements**.

## <a name="see-also"></a>Consulte también
- [Cómo: crear un receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
